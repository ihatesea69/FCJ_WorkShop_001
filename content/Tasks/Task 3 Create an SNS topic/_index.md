+++
title = "Create an SNS Topic"
date = 2023
weight = 3
chapter = false
pre = "<b>3.3 </b>"
+++

## Task 3: Create an SNS Topic

In this task, we'll create an Amazon Simple Notification Service (SNS) topic to facilitate communication between our Lambda functions. This is a crucial step in our serverless architecture for converting blog posts to audio.

### Why Use SNS?

Our application's architecture splits the text-to-speech conversion process into two Lambda functions for several reasons:

1. **Asynchronous Processing**: This allows users to receive immediate confirmation of their post submission without waiting for the audio conversion to complete.

2. **Scalability**: It enables our system to handle posts of varying lengths efficiently, from short snippets to lengthy articles.

3. **Decoupled Architecture**: By separating the post creation and audio conversion processes, we create a more flexible and maintainable system.

SNS acts as the glue between these two functions, enabling seamless communication and triggering the audio conversion process.

### Steps to Create an SNS Topic:

1. **Access SNS in AWS Console**
   - Open the AWS Management Console
   - In the search bar at the top, type "SNS" and select "Simple Notification Service"

2. **Navigate to Topics**
   - In the left navigation pane, choose "Topics"
   - Note: You may need to expand the navigation pane by clicking the menu icon

3. **Create a New Topic**
   - Click "Create topic"
   - Configure the following details:
     - Type: Choose "Standard"
     - Name: Enter "new_posts"
     - Display name: Enter "New Posts"

4. **Finalize Topic Creation**
   - Scroll to the bottom of the page
   - Click "Create topic"

5. **Save the Topic ARN**
   - After creation, you'll see the Topic ARN (Amazon Resource Name)
   - Copy this ARN and save it in a text editor for later use
   - The ARN will look similar to this:
     ```
     arn:aws:sns:us-west-2:123456789012:new_posts
     ```

### Important Note

You'll use this Topic ARN when configuring the Lambda functions in subsequent tasks. It's crucial for establishing the communication link between your functions.

### Next Steps

With your SNS topic created, you're now ready to move on to the next task in building your serverless blog-to-audio application. This SNS topic will play a vital role in triggering the audio conversion process for each new blog post.