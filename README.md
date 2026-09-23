Lab 10 — Deploy Static Web Application Using S3 on AWS
Aim

To deploy a static web application using S3 on AWS and secure it with signed URLs.

Requirements
AWS Account
Amazon S3
Amazon CloudFront
HTML
CSS
Web Browser
Step 1: Create S3 Bucket
Login to the AWS Management Console.
Search for S3.
Click S3.
Click Create bucket.
Select the required AWS Region.
Enter a unique Bucket name.
Under Block Public Access settings, uncheck Block all public access.
Acknowledge the warning.
Keep the remaining settings as default.
Click Create bucket.
Step 2: Enable Static Website Hosting
Open the created S3 bucket.
Click Properties.
Scroll down to Static website hosting.
Click Edit.
Select Enable.
Select Host a static website.
Enter the following as the Index document:
index.html
Click Save changes.
Step 3: Create Website Files

Create the following files:

Lab10/
├── index.html
└── style.css
index.html
<!DOCTYPE html>
<html>
<head>
    <title>Cloud Computing Lab 10</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <h1>Cloud Computing Lab 10</h1>

    <h2>Static Web Application</h2>

    <p>
        This website is deployed using Amazon S3
        and AWS CloudFront.
    </p>

    <button>Welcome to AWS</button>

</body>
</html>
style.css
body {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: lightblue;
    padding-top: 100px;
}

h1 {
    color: darkblue;
}

h2 {
    color: black;
}

p {
    font-size: 20px;
}

button {
    padding: 10px 20px;
    font-size: 16px;
}
Step 4: Add Bucket Policy
Open the S3 bucket.
Click Permissions.
Scroll down to Bucket policy.
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
Step 5: Upload Website Files
Open the S3 bucket.
Click Objects.
Click Upload.
Select:
index.html
style.css
Click Upload.
Verify that both files are displayed in the bucket.
Step 6: Test S3 Website
Go to Properties.
Find Static website hosting.
Copy the Bucket website endpoint.
Open the endpoint in a web browser.
Verify that the website is displayed.
Step 7: Create CloudFront Distribution
Open the AWS Management Console.
Search for CloudFront.
Open CloudFront.
Click Create distribution.
Under Origin domain, use the S3 static website URL.
Remove https:// from the beginning if required.
Set the viewer protocol policy to:
Redirect HTTP to HTTPS
Configure the allowed HTTP methods.
Click Create distribution.
Step 8: Wait for CloudFront Deployment
Open the CloudFront Distributions page.
Find your distribution.
Wait until the distribution status becomes Deployed.
Step 9: Open CloudFront Website
Copy the Distribution domain name.
Open a new browser tab.
Enter the CloudFront URL.

Example:

https://xxxxxxxxxxxx.cloudfront.net
The static website should be displayed.
Step 10: Verify Output

The website should display:

Cloud Computing Lab 10

Static Web Application

This website is deployed using Amazon S3
and AWS CloudFront.

[ Welcome to AWS ]
