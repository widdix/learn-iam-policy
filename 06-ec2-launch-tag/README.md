# Lab 06: Launch EC2 instance with tag

## Introduction

You are using tags to allocate your AWS costs to different cost centers. Therefore, you want to make sure that EC2 instance are not launched without a tag `costcenter`.

Write an IAM policy that allows to launch EC2 instances only when a tag with key ` costcenter` is set.

```
aws ec2 run-instances --tag-specifications "ResourceType=instance,Tags=[{Key=costcenter,Value=test}]" "ResourceType=volume,Tags=[{Key=costcenter,Value=test}]" --instance-type t3.micro --region <Region> --image-id <ImageId> --subnet-id <SubnetId>
```

## Instructions

1. Open [IAM](https://console.aws.amazon.com/iam/home).
1. Search an IAM role with a name equal to the `IamRole` output of your CloudFormation stack.
1. Add an inline policy to your IAM role.
1. Make sure you are logged into the SSH bastion host.

Launching an EC2 instance without any tags should be denied.

```
aws ec2 run-instances --instance-type t3.micro --region <Region> --image-id <ImageId> --subnet-id <SubnetId>
```

But launching an EC2 instance with a tag `costcenter` should work.

```
aws ec2 run-instances --tag-specifications "ResourceType=instance,Tags=[{Key=costcenter,Value=test}]" "ResourceType=volume,Tags=[{Key=costcenter,Value=test}]" --instance-type t3.micro --region <Region> --image-id <ImageId> --subnet-id <SubnetId>
```

Note down the instance id of the launched instance, please.

## Help

* [Actions, Resources, and Condition Keys for Amazon EC2](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonec2.html)
* [Restricting Access to EC2 Instances Based on Tags](https://cloudonaut.io/restricting-access-to-ec2-instances-based-on-tags/)
* `policy.json` includes a sample solution for the necessary IAM policy.

## Clean up

Open the AWS Management Console to:

1. Remove the inline policy from your IAM role.
1. Terminate the EC2 instance you have launched.
