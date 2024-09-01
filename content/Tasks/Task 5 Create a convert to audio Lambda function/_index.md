+++
title = "Create a Convert to Audio Lambda Function"
date = 2023
weight = 5
chapter = false
pre = "<b>3.5 </b>"
+++

## Creating a Lambda Function for Text-to-Audio Conversion

In this step, we'll create a Lambda function that converts text stored in a DynamoDB table into an audio file. This function will be a crucial component in our serverless text-to-speech application.

## Steps to Create the Lambda Function

1. **Navigate to Lambda Functions**
   - In the AWS Management Console, go to the Lambda service.
   - In the left navigation pane, select "Functions".
   - *Note: If the navigation pane is collapsed, click the menu icon to expand it.*

2. **Initiate Function Creation**
   - Click the "Create function" button.

3. **Configure Function Settings**
   - Choose "Author from scratch" for a custom implementation.
   - Use the following configuration:
     - **Function name:** `ConvertToAudio`
     - **Runtime:** Python 3.12
     - **Execution role:** 
       - Expand "Change default execution role"
       - Select "Use an existing role"
       - Choose "Lab-Lambda-Role" from the dropdown

4. **Create the Function**
   - Scroll to the bottom of the page and click "Create function".

5. **Implement the Function Code**
   - In the "Function code" section, you'll see a code editor.
   - Delete any existing code in the editor.
   - Copy and paste the provided Python code (shown below) into the editor.

## Function Code Overview

The Lambda function you're about to create will:
- Retrieve text content from DynamoDB based on a given post ID.
- Split the text into manageable chunks (if necessary).
- Use Amazon Polly to convert each chunk of text into speech.
- Store the resulting audio files in an S3 bucket.

This function is designed to handle long-form content by breaking it into smaller pieces, ensuring that even large articles can be converted to audio efficiently.

Now, let's implement the core functionality of our `ConvertToAudio` Lambda function:
```python
import boto3
import os
from contextlib import closing
from boto3.dynamodb.conditions import Key, Attr

def lambda_handler(event, context):

    postId = event["Records"][0]["Sns"]["Message"]

    print ("Text to Speech function. Post ID in DynamoDB: " + postId)

    # Retrieving information about the post from DynamoDB table
    dynamodb = boto3.resource('dynamodb')
    table = dynamodb.Table(os.environ['DB_TABLE_NAME'])
    postItem = table.query(
        KeyConditionExpression=Key('id').eq(postId)
    )


    text = postItem["Items"][0]["text"]
    voice = postItem["Items"][0]["voice"]

    rest = text

    # Because single invocation of the polly synthesize_speech api can
    # transform text with about 3000 characters, we are dividing the
    # post into blocks of approximately 2500 characters.
    textBlocks = []
    while (len(rest) > 2600):
        begin = 0
        end = rest.find(".", 2500)

        if (end == -1):
            end = rest.find(" ", 2500)

        textBlock = rest[begin:end]
        rest = rest[end:]
        textBlocks.append(textBlock)
    textBlocks.append(rest)

    # For each block, invoke Polly API, which transforms text into audio
    polly = boto3.client('polly')
    for textBlock in textBlocks:
        response = polly.synthesize_speech(
            OutputFormat='mp3',
            Text = textBlock,
            VoiceId = voice
        )

        # Save the audio stream returned by Amazon Polly on Lambda's temp
        # directory. If there are multiple text blocks, the audio stream
        # is combined into a single file.
        if "AudioStream" in response:
            with closing(response["AudioStream"]) as stream:
                output = os.path.join("/tmp/", postId)
                if os.path.isfile(output):
                    mode = "ab"  # Append binary mode
                else:
                    mode = "wb"  # Write binary mode (create a new file)
                with open(output, mode) as file:
                    file.write(stream.read())

    s3 = boto3.client('s3')
    s3.upload_file('/tmp/' + postId,
      os.environ['BUCKET_NAME'],
      postId + ".mp3")
    s3.put_object_acl(ACL='public-read',
      Bucket=os.environ['BUCKET_NAME'],
      Key= postId + ".mp3")

    location = s3.get_bucket_location(Bucket=os.environ['BUCKET_NAME'])
    region = location['LocationConstraint']

    if region is None:
        url_beginning = "https://s3.amazonaws.com/"
    else:
        url_beginning = "https://s3-" + str(region) + ".amazonaws.com/"

    url = url_beginning \
            + str(os.environ['BUCKET_NAME']) \
            + "/" \
            + str(postId) \
            + ".mp3"

    # Updating the item in DynamoDB
    response = table.update_item(
        Key={'id':postId},
          UpdateExpression=
            "SET #statusAtt = :statusValue, #urlAtt = :urlValue",
          ExpressionAttributeValues=
            {':statusValue': 'UPDATED', ':urlValue': url},
        ExpressionAttributeNames=
          {'#statusAtt': 'status', '#urlAtt': 'url'},
    )

    return
```


## Configuring the Lambda Function

After deploying the Lambda function, you need to configure several important settings:

### Setting Environment Variables

1. Select the **Configuration** tab
2. In the left navigation pane, choose **Environment variables**
3. In the Environment variables section, click **Edit**
4. Add the following environment variables:

   | Key | Value |
   |-----|-------|
   | DB_TABLE_NAME | posts |
   | BUCKET_NAME | [Your S3 bucket name, e.g., audioposts-123] |

5. Click **Save**

### Adjusting Maximum Execution Time

1. In the General configuration section, click **Edit**
2. Update the **Timeout** to 5 minutes
3. Click **Save**

### Configuring SNS Trigger

1. In the Triggers section, click **Add trigger**
2. Configure as follows:
   - Select a source: SNS
   - SNS topic: Choose `new_posts` from the available topics
3. Click **Add**

## Testing

You are now ready to test if the two Lambda functions communicate successfully via SNS and create a Polly audio file.

---

## Task Complete

You can now proceed to the next task.



