# Prerequisites<a name="async-prereqs"></a>

The following prerequisites must be met in order for Amazon Translate to perform a successful batch translation job:
+ The Amazon S3 buckets that contain your input and output documents must be in the same AWS Region as the API endpoint you are calling\.
+ The collection of batch input documents must be 5 GB or less in size\.
+ There can be a maximum of one million documents submitted in a batch translation job\.
+ Each input document must be 20 MB or less and must contain fewer than 1 million characters\.
+ Your input files must be in a folder in an Amazon S3 bucket\. If your files are not in a folder, and they reside at the top level of a bucket, Amazon Translate throws an error when you attempt to run a batch translation job\. This requirement applies only to input files\. No folder is necessary for the output files, and Amazon Translate can place them at the top level of an Amazon S3 bucket\.

## Supported File Formats<a name="async-prereqs-formats"></a>

Amazon Translate supports the following types of files for batch translation jobs:
+ Plain text\.
+ HTML\.
+ Word documents \(\.docx\)\.
+ PowerPoint Presentation files \(\.pptx\)\.
+ Excel Workbook files \(\.xlsx\)\.
+ XML Localization Interchange File Format \(XLIFF\) files \(\.xlf\)\. Amazon Translate supports only XLIFF version 1\.2\.

Amazon Translate requires files to be UTF\-8 encoded\.

## Prerequisite Permissions<a name="async-prereqs-permissions"></a>

Before you can run a batch translation job, your AWS account must have a service role in IAM\. This role must have a permissions policy that grants Amazon Translate:
+ Read access to your input folder in Amazon S3\.
+ Read and write access to your output bucket\.

It must also include a trust policy that allows Amazon Translate to assume the role and gain its permissions\. This trust policy must allow the `translate.amazonaws.com` service principal to perform the `sts:AssumeRole` action\.

When you create a batch translation job by using the Amazon Translate console, you have the option to allow Amazon Translate to automatically create this role for you\. When you run a batch translation job by using the AWS CLI or the Amazon Translate API, you provide the Amazon Resource Name \(ARN\) of the role in your request\.

For more information, see [Creating a Role to Delegate Permissions to an AWS Service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html) in the *IAM User Guide*\.

**Example Permissions Policy**  
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

**Example Trust Policy**  
The following trust policy allows Amazon Translate to assume the IAM role that the policy belongs to\.  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "translate.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```