# Lab 06: Grant access to KMS customer managed CMK

## Introduction

You want to use KMS to encrypt sensitive data. A customer managed CMK allows you to control who is able to encrypt and decrypt the data.


Write and IAM policy that allows to encrypt and decrypt sensitive data with a specific customer managed CMK.

```
aws kms encrypt --key-id <KmsKeyId> --region <Region> --plaintext "Sensitive Data" --output text --query CiphertextBlob
aws kms decrypt --ciphertext-blob fileb://encrypted.txt --region <Region> --output text --query Plaintext | base64 -d
```

## Instructions

1. Open [IAM](https://console.aws.amazon.com/iam/home) and go to *Encryption keys*.
1. Create a customer managed CMK:
  1. Choose a unique alias.
  1. Keep the defaults for all the following steps.
  1. Create the key.

The key policy attached to your customer managed CMK enables IAM policies to administer and use the key. To be able to use the key from the SSH bastion host, you need to create an IAM policy which grants access to the encrypt and decrypt actions.

1. Open [IAM](https://console.aws.amazon.com/iam/home).
1. Search an IAM role with a name equal to the `IamRole` output of your CloudFormation stack.
1. Add an inline policy to your IAM role.
1. Make sure you are logged into the SSH bastion host.

Try to encrypt sensitive data.

```
aws kms encrypt --key-id <KmsKeyId> --region <Region> --plaintext "Sensitive Data" --output text --query CiphertextBlob | base64 --decode > encrypted.txt
```

Try to decrypt the data.

```
aws kms decrypt --ciphertext-blob fileb://encrypted.txt --region <Region> --output text --query Plaintext | base64 -d
```

## Help

* [Actions, Resources, and Condition Keys for AWS Key Management Service](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awskeymanagementservice.html)
* [Using Key Policies in AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html)
* [Allows Access to the AWS Account and Enables IAM Policies](https://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html#key-policy-default-allow-root-enable-iam)
* `policy.json` includes a sample solution for the necessary IAM policy.

## Clean up

Open the AWS Management Console to:

1. Remove the inline policy from your IAM role.
1. Delete your customer managed CMK.
