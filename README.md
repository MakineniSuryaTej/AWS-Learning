# AWS-Learning-Progress

## Day 1:

> Introduction
- What's a cloud? A collection of services (databases, virtal servers, etc) which creates a platform.
- The AWS has pay as you go pricing.
- AWS Services

> Security and Identity
- AWS Identity Access Management (IAM), AWS Secrets Manager protects the secrets required, Directory Service provides the directories for the org with specific users.
- IAM practice Lab
1. For this lab there is an AWS account, inside of IAM there are different groups such as Admin, Developers, and Test. Each group has certain set of permissions.
2. Three users are already created and we can check them in the **Users Tab**, And there are also there groups that are created previously named EC2-Admin, EC2-Support, and S3-Support which can be seen under **User groups Tab**.
3. The EC2-Admin has an inline policy (has permissions to describe, start, and stop ec2 instances | also few metrics). The EC2-Support group has managed policy (has permissions to describe ec2 instance and list cloud metrics). The S3-Support has managed policy (has permissions of read only access such get, list and describe object.)
4. So now we have 3 users (U1, U2, U3) and we are going to assign these users to the above groups. First, assign the U1 to the S3-Support group (**Process: Click on the S3-Support group, click on Add Users button, select the U1, and then click on Add Users**). Then we are going to do the same for the U2 and U3. Add the U2 to EC2-Support group and U3 to EC2-Admin group.
5. We can edit permissions of any user (**Process: Click on the user, under the permissions tab expand the policy and click on the edit**).
6. To demonstrate these permissions, **go to the dashboard copy the sign in url and paste it in new tab and login as U1. To check permissions click on S3 and click on create bucket, it fails since U1 does not have permissions and this goes the same with EC2 since U1 has read only permissions**.
7. Similarly we login as U2, here when we click on EC2 and click on instances it works and has more permissions than U1, but when we try to stop that instance it fails. U2 also cannot create or view the buckets.
8. Login as U3, head over to EC2 and if we try to stop the instance it stops since U3 is in the group EC2-Admin. 
