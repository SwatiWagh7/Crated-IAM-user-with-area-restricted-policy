 # Create an IAM User Restricted to the North Virginia (us-east-1) Region Using a JSON Policy.

First, we will create IAM User:
You can create a user either from the AWS Management Console or via AWS CLI
1.	Create IAM user:
-	User
-	Click create user
-	Enter user name
-	Click Next
-	Create user
 <img width="808" height="308" alt="image" src="https://github.com/user-attachments/assets/fddeb371-5dcd-473d-b352-305afff69037" />

2.	Now Create policy for North Virginia Region (us-east-1)
-	Go to Policies
-	Create policy
-	Choose JSON
-	Paste below code: 

### Paste the below code:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyAllRegionsExceptNVirginia",
      "Effect": "Deny",
      "NotAction": [
        "iam:*",
        "organizations:*",
        "account:*"
      ],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:RequestedRegion": "us-east-1"
        }
      }
    }
  ]
}


-	This will deny all other regions accept North Virginia (us-east-1)
-	Give policy name
-	Create policy

 <img width="1001" height="300" alt="image" src="https://github.com/user-attachments/assets/91a46d70-0a01-410d-91c1-ac30e6a79e4e" />

3.	Now attach this policy to IAM use you have created:
-	Go to Users
-	Choose user you have created
-	Go to permissions
-	Add permissions
-	Select attach policies directly
-	Search and select your created policy
-	Next
-	Click add permissions
-	Policy now applied to user you have created


 <img width="1060" height="458" alt="image" src="https://github.com/user-attachments/assets/0192362f-c3ef-44ed-bfbb-b368f4ab218c" />


