+++
title = "Admin User and Group"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

**Contents:**
- [Create an Admin Group](#create-an-admin-group)
- [Create Admin User](#create-admin-user)

#### Create an Admin Group

1. **Sign In to the Console** in [AWS Web Service page](https://aws.amazon.com/)
2. Click your account name on the top right and choose **My Security Credentials**

![Image](/images/1-account-setup/MySecurity.png?width=15pc)

3. In the left bar, choose **Groups** then choose **Create Group**
4. Enter Group Name (Example:AdminGroup) and choose **Next Step**

![Image](/images/1-account-setup/GroupName.png?width=90pc)

5. Attach Policy click choose **AdministratorAccess** then choose **Next Step**

![Image](/images/1-account-setup/GroupPolicy.png?width=90pc)

6. Review your Group name and Policies then choose **Create Group**
   
#### Create Admin User

1. In the left bar, choose **Users** then choose **Add User**
2. Enter User name (Example:Admin) then click choose **Programmatic access** and choose **Next:Permissions**

![Image](/images/1-account-setup/AddUser.png?width=90pc)

3. In tab **Add user to group** choose **AdminGroup** we create before or to choose tab **Attach existing policies directly** and choose **Administrator Access**

![Image](/images/1-account-setup/UserPolicy.png?width=90pc)

4. Choose **Next:Tags**
5. Tags is optional to organize, track, or control access for user, so you can add tags or not.
6. Choose **Next:Review**
7. Check the user details then choose **Create User**
8. After create success, download **.csv** file to store Security Credentials for further features.