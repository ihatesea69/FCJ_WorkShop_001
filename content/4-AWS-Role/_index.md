+++
title = "Create IAM Role"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

You can use IAM roles to delegate access to your AWS resources. With IAM roles, you can establish trust relationships between your trusting account and other AWS trusted accounts.

**Contents:**
- [Create an AWS Role](#create-an-aws-role)

#### Create an AWS Role

1. Sign in to AWS Management Console and open the IAM console at [ https://console.aws.amazon.com/iam/]( https://console.aws.amazon.com/iam/).
2. In the navigation pane of the console, choose **Roles** and then choose **Create role**.
3. Choose the **Another AWS account** role type.
4. For **Account ID**, type the AWS account ID to which you want to grant access to your resources.
5. If you are granting permissions to users from an account that you do not control, and the users will assume this role programmatically, then select **Require external ID**.
6. If you want to restrict the role to users who sign in with multi-factor authentication (MFA), select **Require MFA**.

![Add New Role](/images/1-account-setup/AddRole.png?width=90pc)

7. Choose **Next: Permissions**.
8. IAM includes a list of the AWS managed and customer managed policies in your account. Select the policy to use for the permissions policy or choose **Create policy** to open a new browser tab and create a new policy from scratch. For more information, see step 4 in the procedure [Creating IAM Policies (Console)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html#access_policies_create-start).
9.  (Optional) Set a [permissions boundary](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html).

![Role Policy](/images/1-account-setup/RolePolicy.png?width=90pc)

10. Choose **Next: Tags**.
11. (Optional) Add metadata to the role by attaching tags as key–value pairs.
12. Choose **Next: Review**.
13. For **Role name**, type a name for your role. Role names must be unique within your AWS account. They are not distinguished by case.
14. (Optional) For **Role description**, type a description for the new role.

![Role Review](/images/1-account-setup/RoleReview.png?width=90pc)

15. Review the role and then choose **Create role**.

