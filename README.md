# cloudlab-statics3
Lab 10 — Simple Steps According to Manual

Aim: To deploy a static web application using S3 on AWS and secure it with signed URLs.

Step 1: Create S3 Bucket
Login to AWS Console.
Search for S3.
Click Create bucket.
Select the AWS Region.
Enter a unique Bucket name.
According to the manual, uncheck “Block all public access.”
Keep other settings as default.
Click Create bucket.
Step 2: Enable Static Website Hosting
Open your newly created bucket.
Click Properties.
Scroll down to Static website hosting.
Click Edit.
Enable Static website hosting.
Select Host a static website.
Enter:
index.html
Click Save changes.
Step 3: Add Bucket Policy
Go to Permissions.
Scroll to Bucket policy.
Click Edit.
Paste the following policy.
Replace BUCKET_NAME with your bucket name.
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

This is the policy structure given in the manual.

Step 4: Upload Website
Go to Objects.
Click Upload.
Select your website files, for example:
index.html
style.css
Click Upload.
Step 5: Check S3 Website
Go to Properties.
Find Static website hosting.
Copy the Bucket website endpoint.
Open it in your browser.

Your website should open.

Step 6: Create CloudFront
Search CloudFront in AWS Console.
Click Create distribution.
For Origin domain, use the S3 static website URL.
Remove https:// from the beginning if required, as shown in the manual.
Select:
Redirect HTTP to HTTPS
Configure the allowed HTTP methods.
Click Create distribution.
Step 7: Open CloudFront Website
Wait until CloudFront shows the distribution as deployed.
Copy the Distribution domain name.
Open it in your browser.

Example:

https://xxxxxxxxxxxx.cloudfront.net

Your static website should appear.
