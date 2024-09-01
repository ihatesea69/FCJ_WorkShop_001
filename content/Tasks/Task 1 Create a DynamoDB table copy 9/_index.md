+++
title = "Create a DynamoDB Table"
date = 2021
weight = 1
chapter = false
pre = "<b>3.1 </b>"
+++

## Task 1: Create a DynamoDB Table  

In this task, we'll create an Amazon DynamoDB table to store information about blog posts, including the text content and the URL of the corresponding MP3 file. This table will serve as the backbone of our application's data storage.

### Steps:

1. Navigate to the AWS Management Console.
2. In the search bar at the top, type "DynamoDB" and select it from the results.
3. On the DynamoDB dashboard, click "Create table".
4. Set up the table with the following details:
   - Table name: `posts`
   - Partition key: `id` (String)
   - Table settings: Leave as Default settings
5. Click "Create table" to finalize the process.

### Table Structure

While we don't need to define the entire structure now, our application will eventually store the following information in the DynamoDB table:

- `id`: A unique identifier for each post (String, Primary Key)
- `status`: Indicates whether an MP3 file has been created (String, either "UPDATED" or "PROCESSING")
- `text`: The content of the post to be converted to audio (String)
- `voice`: The Amazon Polly voice used for audio conversion (String)
- `url`: A link to the S3 bucket where the audio file is stored (String)

This table structure will allow our application to efficiently manage and retrieve information about each blog post and its associated audio file.