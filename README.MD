# Deploying a Static Website to Amazon S3

This guide provides steps to deploy your static website to an S3 bucket on AWS.

## Prerequisites

- AWS account
- An S3 bucket created (e.g., `staticbipul`)

## Steps to Deploy

### 1. Prepare Your Static Files

Ensure your static website files (HTML, CSS, JavaScript, images, etc.) are ready in a local directory.

### 2. Configure the S3 Bucket for Static Website Hosting

1. Sign in to the AWS Management Console.
2. Open the Amazon S3 console at [https://s3.console.aws.amazon.com/s3/](https://s3.console.aws.amazon.com/s3/).
3. In the Buckets list, choose the name of the bucket you want to use (e.g., `staticbipul`).
4. Choose the **Properties** tab.
5. In the **Static website hosting** section, choose **Edit**.
6. Select **Enable**.
7. For **Index document**, enter `index.html`.
8. For **Error document**, you can enter `error.html` (optional).
9. Choose **Save changes**.

### 3. Set Bucket Policy for Public Access

1. In the S3 console, go to the **Permissions** tab of your bucket.
2. In the **Bucket Policy** section, choose **Edit**.
3. Add the following policy to make the bucket publicly accessible:

    ```json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "PublicReadGetObject",
                "Effect": "Allow",
                "Principal": "*",
                "Action": "s3:GetObject",
                "Resource": "arn:aws:s3:::staticbipul/*"
            }
        ]
    }
    ```



### enter cors policy also

  ``` json

[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "GET",
            "POST",
            "PUT",
            "DELETE",
            "HEAD"
        ],
        "AllowedOrigins": [
            "*"
        ],
        "ExposeHeaders": [
            "ETag",
            "x-amz-meta-custom-header"
        ],
        "MaxAgeSeconds": 3000
    }
]

```

4. Choose **Save changes**.

### 4. upload the file 
 Inside the s3 buket you willsee the upload option upload the folder 


### 5. Access Your Website

After uploading your files, you can access your static website using the bucket's endpoint.

1. Go back to the **Properties** tab of your S3 bucket.
2. In the **Static website hosting** section, find the **Bucket website endpoint**.
3. Open the endpoint URL in your web browser to view your website.

## Additional Resources

- [AWS S3 Static Website Hosting Documentation](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html)
- [AWS CLI Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)

