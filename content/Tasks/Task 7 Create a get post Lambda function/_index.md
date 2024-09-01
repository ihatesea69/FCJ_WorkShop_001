+++
title = "Create a Get Post Lambda Function"
date = 2023
weight = 7
chapter = false
pre = "<b>3.7 </b>"
+++

## Task 7: Create a Get Post Lambda Function

In this task, we'll create the final Lambda function that provides a method for retrieving information about posts from our DynamoDB database. This function plays a crucial role in our serverless blog-to-audio system by enabling efficient data retrieval.

## Creating the Lambda Function

1. **Navigate to the AWS Management Console**
2. **In the search bar at the top, type "Lambda" and select it**
3. **Click on "Create function"**
4. **Choose "Author from scratch" and use these settings:**
   - **Function name:** `PostReader_GetPost`
   - **Runtime:** Python 3.12
   - **Execution role:** Use an existing role
   - **Existing role:** Lab-Lambda-Role
5. **Scroll down and click "Create function"**

## Adding the Function Code

Replace the existing code in the Lambda function with the following:
```python 
import boto3
import os
from boto3.dynamodb.conditions import Key, Attr

def lambda_handler(event, context):

    postId = event["postId"]

    dynamodb = boto3.resource('dynamodb')
    table = dynamodb.Table(os.environ['DB_TABLE_NAME'])

    if postId=="*":
        items = table.scan()
    else:
        items = table.query(
            KeyConditionExpression=Key('id').eq(postId)
        )

    return items["Items"]
```

This function is very short. It expects to get the post ID (the DynamoDB item ID) and, based on this ID, it retrieves all information (including the S3 link to the audio file if it exists) and then returns it. To make it a little more user-friendly, if the input parameter is an asterisk (*), the Lambda function returns all items from the database. For a database with a lot of items, avoid this approach because it can degrade performance and might take a long time.

### Deploy

Choose **Deploy**.

You need to provide the name of the DynamoDB table as an environment variable for the function.

### Configuring Environment Variables

1. Choose the **Configuration** tab to configure the environment variables.
2. In the left navigation pane, choose **Environment variables**.
3. In the Environment variables section, choose **Edit**.
4. Choose **Add environment variable**.
   - **Key:** Enter `DB_TABLE_NAME`
   - **Value:** Enter `posts`
5. Choose **Save**.

### Testing the Function

1. In the **Test** tab, create your test event using the following parameters:
   - **Event name:** `AllPosts`
   - **Command:** Replace the existing code with the following code:
     ```json
     {
       "postId": "*"
     }
     ```
2. Choose **Save**.
3. Choose **Test** to run the test event.

You should see the message: `Execution result: succeeded`.

If you expand the **Details** section, you should see a list of all records from the DynamoDB table.

### Task Complete

You can now proceed to the next task.
