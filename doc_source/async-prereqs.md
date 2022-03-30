# Prerequisites for batch translation jobs<a name="async-prereqs"></a>

The following prerequisites must be met in order for Amazon Translate to perform a successful batch translation job:
+ The Amazon S3 buckets that contain your input and output documents must be in the same AWS Region as the API endpoint you are calling\.
+ The collection of batch input documents must be 5 GB or less in size\.
+ There can be a maximum of one million documents submitted in a batch translation job\.
+ Each input document must be 20 MB or less and must contain fewer than 1 million characters\.
+ Your input files must be in a folder in an Amazon S3 bucket\. If your files are not in a folder, and they reside at the top level of a bucket, Amazon Translate throws an error when you attempt to run a batch translation job\. This requirement applies only to input files\. No folder is necessary for the output files, and Amazon Translate can place them at the top level of an Amazon S3 bucket\.

## Supported file formats<a name="async-prereqs-formats"></a>

Amazon Translate supports the following types of files for batch translation jobs:
+ Plain text\.
+ HTML\.
+ Word documents \(\.docx\)\.
+ PowerPoint Presentation files \(\.pptx\)\.
+ Excel Workbook files \(\.xlsx\)\.
+ XML Localization Interchange File Format \(XLIFF\) files \(\.xlf\)\. Amazon Translate supports only XLIFF version 1\.2\.

Amazon Translate requires files to be UTF\-8 encoded\.

## Prerequisite permissions<a name="async-prereqs-permissions"></a>

Before you can run a batch translation job, your AWS account must have a service role in IAM\. This role must have a permissions policy that grants Amazon Translate:
+ Read access to your input folder in Amazon S3\.
+ Read and write access to your output bucket\.

It must also include a trust policy that allows Amazon Translate to assume the role and gain its permissions\. This trust policy must allow the `translate.amazonaws.com` service principal to perform the `sts:AssumeRole` action\.

When you create a batch translation job by using the Amazon Translate console, you have the option to allow Amazon Translate to automatically create this role for you\. When you run a batch translation job by using the AWS CLI or the Amazon Translate API, you provide the Amazon Resource Name \(ARN\) of the role in your request\.

For more information, see [Creating a Role to Delegate Permissions to an AWS Service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html) in the *IAM User Guide*\.

**Example Permissions policy**  
The following example permissions policy grants read access to an input folder in an Amazon S3 bucket\. It grants read and write access to an output bucket\.  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": [
        "arn:aws:s3:::input-bucket-name/*",
        "arn:aws:s3:::output-bucket-name/*"
      ]
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": [
        "arn:aws:s3:::input-bucket-name",
        "arn:aws:s3:::output-bucket-name"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::output-bucket-name/*"
    }
  ]
}
```

**Example Trust policy**  
The following trust policy allows Amazon Translate to assume the IAM role that the policy belongs to\.  
We recommend that you verify the AWS account that is using the trust policy, to mitigate the [ Confused deputy](https://docs.aws.amazon.com/IAM/latest/UserGuide/confused-deputy.html) problem\. This example uses the aws:SourceArn and aws:SourceAccount condition keys to verify the source account\. Enter the AWS account that submits the batch translation job\.   

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "translate.amazonaws.com"
      },
      "Action": "sts:AssumeRole",
      "Condition": {
        "ArnLike": {
            "aws:SourceArn": "arn:aws:translate:*:111122223333:*"
        },
        "StringEquals": {
            "aws:SourceAccount": "111122223333"
        }
      }
    }
  ]
}
```

## Prerequisite permissions to customize encryption<a name="async-prereqs-permissions-custom-encryption"></a>

You can customize your encryption settings in Amazon Translate, but first you must add permissions to the service role in IAM\.

Amazon Translate encrypts the translation output that you produce when you run a batch translation job\. By default, it does this encryption with an *AWS managed key*\. This type of key is created by AWS and stored in AWS Key Management Service \(AWS KMS\) in your account\. However, you cannot manage this KMS key yourself\. It is managed and used on your behalf only by AWS\.

Optionally, you can choose to encrypt your output with a *customer managed key*, which is a KMS key that you create, own, and manage in your AWS account\. 

Your key must have a key policy that enables Amazon Translate to use it\. The key policy does this by granting its permissions to the service role that allows Amazon Translate to access your Amazon S3 bucket\. 

The key policy allows the service role to perform the AWS KMS operations that are required to encrypt your output, as shown by the following example policy statement\. 

**Example KMS key policy statement**  

```
{
  "Effect": "Allow",
  "Principal":
  {
    "AWS":
    [
      "arn:aws:iam::111122223333:role/AmazonTranslateServiceRoleS3FullAccess"
    ]
  },
  "Action":
  [
    "kms:Decrypt",
    "kms:GenerateDataKey",
    "kms:CreateGrant",
    "kms:RetireGrant",
    "kms:DescribeKey"
  ],
  "Resource": "*"
}
```

For more information, see [Key policies in AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html) in the *AWS Key Management Service Developer Guide*

### Permissions to use an AWS KMS key from another AWS account<a name="async-prereqs-permissions-custom-encryption-cross-account"></a>

If you want to use a KMS key that's in a different AWS account from the one where you use Amazon Translate, then you must: 

1. Update the service role for Amazon Translate in IAM\.

1. Update the key policy in AWS KMS\.

To update your service role, attach a policy that allows it to perform the necessary AWS KMS operations with the KMS key that's in the other AWS account, as shown by the following example\.

**Example IAM policy to grant access to a KMS key in a different account**  

```
{
  "Effect": "Allow",
  "Action":
  [
    "kms:Decrypt",
    "kms:GenerateDataKey",
    "kms:CreateGrant",
    "kms:RetireGrant",
    "kms:DescribeKey"
  ],
  "Resource": "arn:aws:kms:us-west-2:111122223333:key/key-id"
}
```

To update your KMS key policy, add the service role and root user as principals that are allowed to use the key, as shown by the following example policy statement\.

**Example KMS key policy statement to allow an IAM role to use the key**  

```
{
  "Effect": "Allow",
  "Principal":
  {
    "AWS":
    [
      "arn:aws:iam::444455556666:role/AmazonTranslateServiceRoleS3FullAccess",
      "arn:aws:iam::444455556666:root"
    ]
  },
  "Action":
  [
    "kms:Decrypt",
    "kms:CreateGrant",
    "kms:GenerateDataKey",
    "kms:RetireGrant",
    "kms:DescribeKey"
  ],
  "Resource": "*"
}
```

For more information, see [Allowing users in other accounts to use a KMS key](https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-modifying-external-accounts.html) in the *AWS Key Management Service Developer Guide*