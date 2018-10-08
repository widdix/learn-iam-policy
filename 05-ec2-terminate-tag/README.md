# Lab 05: Terminate EC2 instance with tag

## Introduction

You want to make sure that engineers are not allowed to terminate EC2 instances running production workloads. Therefore, an engineer should only be allowed to terminate instances that are tagged with `environment = test`.

Write an IAM policy that only allows to terminate instances with a specific tag key and tag value.

```
aws ec2 terminate-instances --region <Region> --instance-ids <InstanceId>
```

## Instructions


1. Launch an instance and add a unique tag (Key = Name, Value = ...). Note down the instance id, please.
1. Open [IAM](https://console.aws.amazon.com/iam/home).
1. Search an IAM role with a name equal to the `IamRole` output of your CloudFormation stack.
1. Add an inline policy to your IAM role.
1. Make sure you are logged into the SSH bastion host.

Try to terminate the your newly launched instance.

```
aws ec2 terminate-instances --region <Region> --instance-ids <InstanceId>
```

Should fail, as the instance is not tagged with `environment = test` yet. Go to the Management Console and add a tag `environment = test` to your instance.

Try to terminate the instance again!

```
aws ec2 terminate-instances --region <Region> --instance-ids <InstanceId>
```


## Help

* [Actions, Resources, and Condition Keys for Amazon EC2](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonec2.html)
* [Restricting Access to EC2 Instances Based on Tags](https://cloudonaut.io/restricting-access-to-ec2-instances-based-on-tags/)
* `policy.json` includes a sample solution for the necessary IAM policy.

## Clean up

1. Remove the inline policy from your IAM role.
