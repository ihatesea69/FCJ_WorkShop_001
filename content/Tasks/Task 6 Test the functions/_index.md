+++
title = "Test the Functions"
date = 2023
weight = 6
chapter = false
pre = "<b>3.6 </b>"
+++

## Task 6: Test the Functions

In this crucial task, we'll verify the functionality of our serverless blog-to-audio conversion system. We'll test the entire workflow, from triggering the initial Lambda function to confirming the creation of the audio file in S3.

## Workflow Overview

1. Manually trigger the New Post Lambda function
2. Function stores data in DynamoDB and sends a message to the SNS topic
3. SNS triggers the Convert To Audio function
4. Convert To Audio function uses Amazon Polly to create an audio file
5. Audio file is stored in the S3 bucket

## Step-by-Step Testing Process

### 1. Trigger the New Post Lambda Function

1. Navigate to the AWS Lambda console
2. Locate and select the `PostReader_NewPost` function
3. Click the "Test" button
4. Verify the success message: "Execution result: succeeded"

### 2. Confirm DynamoDB Entry

1. Open the AWS DynamoDB console
2. In the navigation pane, choose "Explore items"
3. Select the "posts" table
4. Verify the presence of two entries (due to running the test twice)
5. Note the `url` field in the second entry, indicating successful audio conversion

### 3. Check Convert to Audio Function Execution

1. Return to the AWS Lambda console
2. Select the `ConvertToAudio` function
3. Navigate to the "Monitor" tab
4. Examine the monitoring charts for function invocation

> **⚠️ Warning:** If you encounter errors:
> - Check the "Error count and success rate" chart
> - View CloudWatch logs for detailed error messages
> - Common issues: Incorrect S3 bucket name in environment variables

### 4. Verify Audio File in S3

1. Open the AWS S3 console
2. Locate and select your `audioposts-` bucket
3. Confirm the presence of an MP3 file
4. Download and play the file - you should hear Polly's Joanna voice saying "This is working!"

## Troubleshooting Tips

- Double-check all IAM permissions
- Ensure SNS topic and subscription are correctly configured
- Verify environment variables in Lambda functions
- Review CloudWatch logs for detailed error information

## Next Steps

Congratulations on successfully testing your serverless blog-to-audio conversion system! In the next task, we'll explore ways to enhance and optimize your application.

---

🎉 **Task Complete!** You've verified the core functionality of your serverless application. Proceed to the next exciting challenge in your AWS journey!