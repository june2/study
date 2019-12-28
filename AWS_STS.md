# AWS Security Token Service (AWS STS)
- AWS Security Token Service (AWS STS) is the service that you can use to create and provide trusted users with temporary security credentials that can control access to your AWS resources. Temporary security credentials work almost identically to the long-term access key credentials that your IAM users can use.


![image](https://user-images.githubusercontent.com/5827617/71540983-73546c80-2995-11ea-92c5-a2759f136ba6.png)

- In this diagram, IAM user Alice in the Dev account (the role-assuming account) needs to access the Prod account (the role-owning account). 
- How it works:
   1. Alice in the Dev account assumes an IAM role (WriteAccess) in the Prod account by calling AssumeRole.
   2. STS returns a set of temporary security credentials.
   3. Alice uses the temporary security credentials to access services and resources in the Prod account. 
      Alice could, for example, make calls to Amazon S3 and Amazon EC2, which are granted by the WriteAccess role.
