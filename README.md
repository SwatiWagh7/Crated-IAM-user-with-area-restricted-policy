# Create an IAM User Restricted to the North Virginia (us-east-1) Region Using a JSON Policy.

First, we will create IAM User:
You can create a user either from the AWS Management Console or via AWS CLI
1.	Create IAM user:
-	User
-	Click create user
-	Enter user name
-	Click Next
-	Create user
 

2.	Now Create policy for North Virginia Region (us-east-1)
-	Go to Policies
-	Create policy
-	Choose JSON
-	Paste below code: 

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

 

