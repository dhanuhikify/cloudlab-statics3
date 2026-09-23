# Lab 10 — Deploy Static Web Application Using S3 on AWS

## Aim

To deploy a static web application using S3 on AWS and secure it with signed URLs.

## Step 1: Create S3 Bucket

1. Login to **AWS Console**.
2. Search for **S3**.
3. Click **Create bucket**.
4. Select the AWS **Region**.
5. Enter a unique **Bucket name**.
6. Uncheck **Block all public access**.
7. Keep other settings as default.
8. Click **Create bucket**.

## Step 2: Enable Static Website Hosting

1. Open the newly created bucket.
2. Click **Properties**.
3. Find **Static website hosting**.
4. Click **Edit**.
5. Enable **Static website hosting**.
6. Select **Host a static website**.
7. Enter the following as the Index document:

```text
index.html
Click Save changes.
Step 3: Add Bucket Policy
Go to Permissions.
Find Bucket policy.
Click Edit.
Add the following policy.
Replace BUCKET_NAME with your actual bucket name.
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:*",
      "Resource": [
        "arn:aws:s3:::BUCKET_NAME/*",
        "arn:aws:s3:::BUCKET_NAME"
      ]
    }
  ]
}
Click Save changes.
Step 4: Upload Website
Go to Objects.
Click Upload.
Select the website files:
index.html
style.css
Click Upload.
Step 5: Check S3 Website
Go to Properties.
Find Static website hosting.
Copy the Bucket website endpoint.
Open the endpoint in a web browser.
Check whether the website is displayed.
Step 6: Create CloudFront Distribution
Search for CloudFront in AWS Console.
Click Create distribution.
For Origin domain, use the S3 static website URL.
Remove https:// from the beginning if required.
Select:
Redirect HTTP to HTTPS
Configure the allowed HTTP methods.
Click Create distribution.
Step 7: Open CloudFront Website
Wait until the CloudFront distribution is Deployed.
Copy the Distribution domain name.
Open it in a web browser.

Example:

https://xxxxxxxxxxxx.cloudfront.net
The static website should be displayed.
Result

Thus, the static web application was successfully deployed using Amazon S3 and CloudFront.


This follows the **Lab 10 sequence in your uploaded manual**: S3 bucket → static website hosting → bucket policy → uplo
