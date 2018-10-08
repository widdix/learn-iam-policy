# learn-iam-policy

Labs helping you to learn how write IAM policies following the least privilege principle.

## Introduction

We are using `<Variable>` to indicate that you should replace parts of the instructions with a variable.

## Requirements

A SSH bastion host is the starting point for all labs. You don't need to install anything on your local machine. A SSH client is all you need.

## Preparing the lab environment

The CloudFormation template creates a lab environment consisting of:

* SSH bastion host: EC2 Instance with an IAM role and a Security Group attached
* S3 bucket
* SSM parameters

1. Create or upload your EC2 Key Pair.
1. Create a CloudFormation stack based on the template `lab-environment.yml`. Use a stack name including `a-z`, `0-9`, and `-` only.
1. Make a note with the outputs of the stack: `PublicIp, PrivateIp, InstanceId, IamRole, S3Bucket`.
1. Connect to the SSH bastion host: `ec2-user@<PublicIp>` or `ec2-user@<PrivateIp>`.

## Labs

* [Lab 01: S3 read access](https://github.com/widdix/learn-iam-policy/tree/master/01-s3-read)
* [Lab 02: S3 read and write with prefix](https://github.com/widdix/learn-iam-policy/tree/master/02-s3-prefix)
* [Lab 03: Parameter Store read access](https://github.com/widdix/learn-iam-policy/tree/master/03-parameterstore-path)
* [Lab 04: Grant access to KMS customer managed CMK](https://github.com/widdix/learn-iam-policy/tree/master/04-kms-cmk)
* [Lab 05: Terminate EC2 instance with tag](https://github.com/widdix/learn-iam-policy/tree/master/05-ec2-terminate-tag)
* [Lab 06: Launch EC2 instance with tag](https://github.com/widdix/learn-iam-policy/tree/master/05-ec2-terminate-tag)

## Clean up

1. Empty your S3 bucket `<S3Bucket>`.
1. Delete your CloudFormation stack.
