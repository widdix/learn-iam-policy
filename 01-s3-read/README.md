# Lab 01: S3 read access

## Introduction

During bootstrapping your EC2 instance needs to download several artifacts from S3. Therefore, you are using the AWS CLI to synchronize all objects from an S3 bucket with a local folder on your instance. Replace <S3Bucket> with the output `S3Bucket` of your CloudFormation stack.

Write an IAM policy that allows you to synchronize all objects from a specific S3 bucket.

`aws s3 sync s3://<S3Bucket> ~/`

Make sure, you don't allow access to any other S3 buckets.

## Instructions

1. Open [S3](https://s3.console.aws.amazon.com/s3/home). Search for a bucket with a name equal to the `S3Bucket` output of your CloudFormation stack and upload a few files.
1. Open [IAM](https://console.aws.amazon.com/iam/home).
1. Search an IAM role with a name equal to the `IamRole` output of your CloudFormation stack.
1. Add an inline policy to your IAM role.
1. Make sure you are logged into the SSH bastion host.

Now it is time to test weather the EC2 instance is allowed to list and download all objects from your S3 bucket.

`aws s3 sync s3://<S3Bucket> ~/`

## Help

* [Actions, Resources, and Condition Keys for Amazon S3](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazons3.html)
* `policy.json` includes a sample solution for the necessary IAM policy.

## Clean up

1. Remove the inline policy from your IAM role.
