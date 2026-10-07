# Static-web-app-using-s3-AWS

## Aim

To deploy a static web application using **Amazon S3** and secure/access it using **CloudFront**.

## Technologies Used

- Amazon S3
- Amazon CloudFront
- AWS Management Console
- HTML
- CSS
- JavaScript

## Experiment Setup

In this experiment, a static web application is deployed using an **Amazon S3 bucket**.

The S3 bucket is configured for **static website hosting**, and the website files are uploaded to the bucket. **Amazon CloudFront** is then connected to the S3 website to provide faster content delivery with lower latency.

---

## Procedure

### Step 1: Create an AWS S3 Bucket

1. Login to the **AWS Management Console**.
2. Open **S3**.
3. Click **Create bucket**.
4. Select the required AWS Region.
5. Enter a unique **Bucket name**.
6. Uncheck **Block all public access**.
7. Leave the remaining settings as default.
8. Click **Create bucket**.

---

### Step 2: Enable Static Website Hosting

1. Open the newly created S3 bucket.
2. Go to the **Properties** tab.
3. Scroll down to **Static website hosting**.
4. Click **Edit**.
5. Enable static website hosting.
6. Configure the required settings.
7. Save the changes.

The S3 bucket will now provide a **static website endpoint**.

---

### Step 3: Configure the Bucket Policy

1. Open the S3 bucket.
2. Go to the **Permissions** tab.
3. Find **Bucket policy**.
4. Click **Edit**.
5. Add the following policy.
6. Replace `BUCKET_NAME` with your actual bucket name.
7. Click **Save changes**.

```json
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

### Step 4: Upload Website Files
1. Open the S3 bucket.
2. Click Upload.
3. Add your website files.
4. Example files include:

    index.html
    styles.css
    script.js

5. Click Upload.
The static website can now be accessed using the S3 static website URL.

### Step 5: Create a CloudFront Distribution
CloudFront is used to deliver the static website with better performance and lower latency.
1. Open CloudFront from the AWS Management Console.
2. Click Create distribution.
3. Copy the S3 static website URL from the S3 bucket properties.
4. Enter the URL as the Origin domain.
5. Remove https:// from the beginning of the URL if required.
6. Set the Viewer Protocol Policy to:
Redirect HTTP to HTTPS

7. Select the required Allowed HTTP methods.
8. Click Create distribution.

### Step 6: Access the Website

1. Wait for the CloudFront distribution to be created.
2. Open the CloudFront distribution.
3. Copy the Distribution domain name.
4. Open the domain name in a web browser.
The static web application can now be accessed through CloudFront.

## Result

The static web application was successfully deployed using Amazon S3 and accessed through Amazon CloudFront.

## Conclusion

This experiment demonstrates how Amazon S3 can be used to host a static web application and how Amazon CloudFront can be used to distribute the website efficiently with improved performance and lower latency.

## Cleanup

If the resources were created only for learning purposes, delete the AWS resources after completing the experiment to avoid unnecessary AWS charges.
After deleting the resources, the website will no longer be available.
```

