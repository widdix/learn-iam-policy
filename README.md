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
