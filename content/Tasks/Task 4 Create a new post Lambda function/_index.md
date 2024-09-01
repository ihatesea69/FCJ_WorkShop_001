+++
title = "Create a New Post Lambda Function"
date = 2023
weight = 4
chapter = false
pre = "<b>3.4 </b>"
+++

## Task 4: Create a New Post Lambda Function

In this task, we'll create the first Lambda function for our application. This function serves as the entry point, receiving information about new posts that need to be converted into audio files.

### Why Lambda?

AWS Lambda allows us to run code without provisioning or managing servers. It's ideal for our use case because:

1. It's cost-effective - we only pay for the compute time we consume.
2. It scales automatically with the number of requests.
3. It integrates seamlessly with other AWS services like DynamoDB and SNS.

### Steps to Create the Lambda Function:

1. **Access Lambda in AWS Console**
   - Open the AWS Management Console
   - In the search bar at the top, search for and choose "Lambda"

2. **Create a New Function**
   - Click "Create function"
   - Choose "Author from scratch"
   - Configure the following settings:
     - Function name: `PostReader_NewPost`
     - Runtime: Python 3.12
     - Execution role: Use an existing role
     - Existing role: Choose `Lab-Lambda-Role`
   - Click "Create function"

3. **Add Function Code**
   - In the Function code section, delete the existing code
   - Paste the following Python code:

   ```python
   import boto3
   import os
   import uuid

   def lambda_handler(event, context):

       recordId = str(uuid.uuid4())
       voice = event["voice"]
       text = event["text"]

       print('Generating new DynamoDB record, with ID: ' + recordId)
       print('Input Text: ' + text)
       print('Selected voice: ' + voice)

       # Creating new record in DynamoDB table
       dynamodb = boto3.resource('dynamodb')
       table = dynamodb.Table(os.environ['DB_TABLE_NAME'])
       table.put_item(
           Item={
               'id' : recordId,
               'text' : text,
               'voice' : voice,
               'status' : 'PROCESSING'
           }
       )

       # Sending notification about new post to SNS
       client = boto3.client('sns')
       client.publish(
           TopicArn = os.environ['SNS_TOPIC'],
           Message = recordId
       )

       return recordId
   ```

4. **Examine the Code**
   The Lambda function performs the following tasks:
   - Retrieves two input parameters:
     - Voice: One of dozens of voices supported by Amazon Polly
     - Text: The content of the post to be converted into an audio file
   - Creates a new record in the DynamoDB table with information about the new post
   - Publishes information about the new post to SNS (the post ID is published as a message)
   - Returns the ID of the DynamoDB item to the user

5. **Deploy the Function**
   - Click "Deploy" to save your changes

6. **Configure Environment Variables**
   - Navigate to the "Configuration" tab
   - In the left navigation pane, choose "Environment variables"
   - Click "Edit" and add the following variables:
     - Key: `SNS_TOPIC`, Value: [Paste your SNS topic ARN]
     - Key: `DB_TABLE_NAME`, Value: `posts`
   - Click "Save"

7. **Update Function Configuration**
   - In the left navigation pane of the Configuration tab, choose "General configuration"
   - Click "Edit"
   - Update the Timeout to 10 seconds
   - Click "Save"

### Testing the Lambda Function

1. **Create a Test Event**
   - Navigate to the "Test" tab
   - Configure a new test event with the following details:
     - Event name: Joanna
     - Event JSON:
     ```json
     {
       "voice": "Joanna",
       "text": "This is working!"
     }
     ```
   - Click "Save"

2. **Run the Test**
   - Click "Test" to execute your test event
   - You should see a "Execution result: succeeded" message
   - Expand the "Details" section to view the execution log

Congratulations! You've successfully created and tested the New Post Lambda function. This function will serve as the entry point for your application, handling new post submissions and initiating the audio conversion process.