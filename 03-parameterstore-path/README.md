# Lab 03: Parameter Store read access

## Introduction

Your application running on EC2 instances is loading it's configuration parameters from the AWS Systems Manager Parameter Store.

Write an IAM policy that allows to read all parameters by a specific path.

```
aws ssm get-parameters-by-path --region <Region> --path /<CloudFormationStackName>/a/ 
```

## Instructions

1. Open [IAM](https://console.aws.amazon.com/iam/home).
1. Search an IAM role with a name equal to the `IamRole` output of your CloudFormation stack.
1. Add an inline policy to your IAM role.
1. Make sure you are logged into the SSH bastion host.

Getting all parameters from path `/.../a/` should work.

```
aws ssm get-parameters-by-path --region <Region> --path /<CloudFormationStackName>/a/ 
```

Getting parameters from path `/.../b/` should be denied.

```
aws ssm get-parameters-by-path --region <Region> --path /<CloudFormationStackName>/b/ 
```

## Help

**Warning: It might take several minutes until changes to an IAM policy becomes effective.**

* [Actions, Resources, and Condition Keys for Amazon Simple Systems Manager](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsimplesystemsmanager.html#amazonsimplesystemsmanager-parameter)
* `policy.json` includes a sample solution for the necessary IAM policy.

## Clean up

1. Remove the inline policy from your IAM role.
