+++
title = "Setting up an AWS account"
date = 2021
weight = 1
chapter = false
+++

# Creating your first AWS account

#### Overview
In this first lab, you will be creating your new **AWS** account and use Multi-factor Authentication (**MFA**) to improve your account security. Next, you will create an **Administrator Group** and **Admin User** to manage access to resources in your account instead of using the root user. \
Finally, we will step through account authentication with **AWS Support** in the event you experience authentication problems.

#### AWS Account
**An AWS account** is the basic container for all the AWS resources you can create as an AWS customer. By default, each AWS account will have a _root user_. The _root user_ has full access within your AWS account, and root user permissions cannot be limited. When you first create your AWS account, you will be assessing it as the _root user_.

{{% notice note%}}
As a best practice, do not use the AWS account _root user_ for any task where it's not required. Instead, create a new IAM user for each person that requires administrator access. Thereafter, the users in the administrators user group should set up the user groups, users, and so on, for the AWS account. All future interaction should be through the AWS account's users and their own keys instead of the root user. However, to perform some account and service management tasks, you must log in using the root user credentials.
{{% /notice%}}

#### Multi-Factor Authentication (MFA)
**MFA** adds extra security because it requires users to provide unique authentication from an AWS supported MFA mechanism in addition to their regular sign-in credentials when they access AWS websites or services.

#### IAM User Group 
An **IAM user group** is a collection of IAM users. User groups let you specify permissions for multiple users, which can make it easier to manage the permissions for those users. Any user in that user group automatically has the permissions that are assigned to the user group. 

#### IAM User
An **IAM user** is an entity that you create in AWS to represent the person or application that uses it to interact with AWS. A user in AWS consists of a name and credentials. \
Please note that an IAM user with administrator permissions is not the same thing as the AWS account root user.


#### AWS Support
AWS Basic Support offers all AWS customers access to our Resource Center, Service Health Dashboard, Product FAQs, Discussion Forums, and Support for Health Checks – at no additional charge. Customers who desire a deeper level of support can subscribe to AWS Support at the Developer, Business, or Enterprise level.

Customers who choose AWS Support gain one-on-one, fast-response support from AWS engineers. The service helps customers use AWS's products and features. With pay-by-the-month pricing and unlimited support cases, customers are freed from long-term commitments. Customers with operational issues or technical questions can contact a team of support engineers and receive predictable response times and personalized support.


#### Main Content

1. [Creating a new AWS Account](1-create-new-aws-account/)
2. [Setting up MFA for the AWS Account root user](2-MFA-Setup-For-AWS-User-(root))
3. [Creating an Administrator Accounts and Groups](3-create-admin-user-and-group/)
4. [Getting support for Account Authentication](4-verify-new-account/)
<!-- need to remove parenthesis for path in Hugo 0.88.1 for Windows-->