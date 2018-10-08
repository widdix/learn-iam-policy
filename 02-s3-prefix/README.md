# Lab 02: S3 read and write with prefix

## Introduction

Several EC2 instances are uploading backups to an S3 bucket. You want to make sure that each EC2 instance is only allowed to upload and download files to with a specific prefix (also known as folder).

Write an IAM policy that allows you to upload and download objects with prefix `/test/` to your S3 bucket. Make sure, you don't allow access to any other S3 buckets or with another prefix than `/test`.

Actions that should be allowed:

```
aws s3 cp test.txt s3://<S3Bucket>/test/test.txt
aws s3 cp s3://<S3Bucket>/test/test.txt test.txt
```

Actions that should be rejected:
```
aws s3 cp test.txt s3://<S3Bucket>/badprefix/test.txt
aws s3 cp test.txt s3://<BadS3Bucket>/test/test.txt
```

## Instructions

1. Open [S3](https://s3.console.aws.amazon.com/s3/home). Search for a bucket with a name equal to the `S3Bucket` output of your CloudFormation stack and upload a few files.
1. Open [IAM](https://console.aws.amazon.com/iam/home).
1. Search an IAM role with a name equal to the `IamRole` output of your CloudFormation stack.
1. Add an inline policy to your IAM role.
1. Make sure you are logged into the SSH bastion host.

Now it is time to test weather the EC2 instance is allowed to list and download all objects from your S3 bucket.

```
aws s3 cp test.txt s3://<S3Bucket>/test/test.txt
aws s3 cp s3://<S3Bucket>/test/test.txt test.txt
```

The following upload should be rejected.

```
aws s3 cp test.txt s3://<S3Bucket>/badprefix/test.txt
```

## Help

* [Actions, Resources, and Condition Keys for Amazon S3](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazons3.html)
* `policy.json` includes a sample solution for the necessary IAM policy.

## Clean up

1. Remove the inline policy from your IAM role.
