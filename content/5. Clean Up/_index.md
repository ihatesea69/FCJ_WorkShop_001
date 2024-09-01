+++
title = "Clean Up"
date = 2020-05-14T00:38:32+07:00
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

## Clean Up

If you participated in an AWS-hosted event, you don't need to worry about cleaning up any resources. AWS will handle the cleanup process for you.

However, if you ran this workshop in your own AWS account, it's important to delete the CloudFormation stack to avoid any unexpected charges on your AWS bill. Follow these steps to clean up your resources:

1. Open the [AWS CloudFormation Console](https://console.aws.amazon.com/cloudformation/).

2. Select the stack you created for this workshop (e.g., `polly-serverless-stack`).

3. Click on the "Delete" button at the top of the stack details page.

4. In the confirmation dialog, click "Delete stack" to confirm the deletion.

5. Wait for the stack deletion process to complete. This may take a few minutes.

6. Once the stack is deleted, all associated resources will be removed from your account.

By following these steps, you ensure that all resources created during the workshop are properly cleaned up, preventing any unnecessary costs.

Remember, it's always a good practice to review your AWS account regularly and remove any unused resources to maintain a clean and cost-effective environment.