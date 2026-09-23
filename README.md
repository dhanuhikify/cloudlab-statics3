Lab 10 — Deploy Static Web Application Using S3 on AWS
Aim

To deploy a static web application using S3 on AWS and secure it with signed URLs.

Requirements
AWS Account
Amazon S3
Amazon CloudFront
HTML file
CSS file
Web Browser
Step 1: Create an S3 Bucket
Login to the AWS Management Console.
Search for S3.
Open Amazon S3.
Click Create bucket.
Select the required AWS Region.

Enter a unique Bucket name.

Example:

cloud-computing-lab10-2026
Under Block Public Access settings, uncheck Block all public access as specified in the lab manual.
Acknowledge the warning.
Keep the remaining settings as default.
Click Create bucket.
Step 2: Enable Static Website Hosting
Open the newly created S3 bucket.
Click the Properties tab.
Scroll down to Static website hosting.
Click Edit.
Select Enable.
Select Host a static website.

In Index document, enter:

index.html
Click Save changes.
Step 3: Add Bucket Policy
Open the Permissions tab.
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
Step 4: Create Website Files

Create a file named:

index.html

Add the following code:

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

Create another file named:

style.css

Add:

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

The files should be:

Lab10/
├── index.html
└── style.css
Step 5: Upload Website Files to S3
Open your S3 bucket.
Select Objects.
Click Upload.

Select:

index.html
style.css
Click Upload.
Verify that both files are displayed under Objects.
Step 6: Test the S3 Website
Go to the Properties tab.
Find Static website hosting.
Copy the Bucket website endpoint.
Open the endpoint in a web browser.
The website should be displayed.
Step 7: Create CloudFront Distribution
Go to the AWS Console.
Search for CloudFront.
Open CloudFront.
Click Create distribution.
Under Origin domain, enter the S3 static website endpoint.
Remove https:// from the beginning if required.

Set the viewer protocol policy to:

Redirect HTTP to HTTPS
Configure the allowed HTTP methods.
Click Create distribution.
Step 8: Access the Website Through CloudFront
Wait for the CloudFront distribution to become Deployed.
Copy the Distribution domain name.
Open a new browser tab.
Enter the CloudFront URL.

Example:

https://xxxxxxxxxxxx.cloudfront.net
The static website should be displayed.
Step 9: Verify the Website

The website should display:

Cloud Computing Lab 10

Static Web Application

This website is deployed using Amazon S3
and AWS CloudFront.

[ Welcome to AWS ]
Result

Thus, the static web application was successfully deployed using Amazon S3 and accessed through Amazon CloudFront.
