# learn-iam-policy

Labs helping you to learn how write IAM policies following the least privilege principle.

## Introduction

We are using `<Variable>` to indicate that you should replace parts of the instructions with a variable.

## Preparing the lab environment

The CloudFormation template `lab-environment.yml` creates a lab environment consisting of:

* EC2 Instance with an IAM role attached (*access to SSM is granted for Session Manager access*)
* S3 bucket
* SSM parameters

1. Create a CloudFormation stack based on the template `lab-environment.yml`.
    1. Set stack name to your name but only use characters `a-z` (lowercase!).
1. Make a note with the outputs of the stack: `IamRole`, `S3Bucket`.
1. Connect to the EC2 instance using SSM Session Manager
    1. Visit https://console.aws.amazon.com/systems-manager/session-manager/start-session
    1. Select your instance
    1. Push the **Start Session** button
    1. Jump to your home directory: `cd ~`
1. Done. You can now start with the labs.

## Labs

* [Lab 01: S3 read access](https://github.com/widdix/learn-iam-policy/tree/master/01-s3-read)
* [Lab 02: S3 read and write with prefix](https://github.com/widdix/learn-iam-policy/tree/master/02-s3-prefix)
* [Lab 03: Parameter Store read access](https://github.com/widdix/learn-iam-policy/tree/master/03-parameterstore-path)
* [Lab 04: Grant access to KMS customer managed CMK](https://github.com/widdix/learn-iam-policy/tree/master/04-kms-cmk)
* [Lab 05: Terminate EC2 instance with tag](https://github.com/widdix/learn-iam-policy/tree/master/05-ec2-terminate-tag)
* [Lab 06: Launch EC2 instance with tag](https://github.com/widdix/learn-iam-policy/tree/master/06-ec2-launch-tag)

## Clean up

1. Empty your S3 bucket `<S3Bucket>`.
1. Delete your CloudFormation stack.

## More Labs

We offer AWS workshops tailored to your needs. See [widdix/learn-*](https://github.com/widdix?q=learn-) for more labs.
