# Adding your parallel data to Amazon Translate<a name="customizing-translations-parallel-data-adding"></a>

To add parallel data to Amazon Translate, you import a parallel data input file from Amazon S3\. Afterwards, you can use the parallel data to customize the output produced by a batch translation job\.

**Prerequisites**  
Before you can add parallel data to Amazon Translate, you must:  
Have a parallel data input file\. To create one, see [Parallel data input files for Amazon Translate](customizing-translations-parallel-data-input-files.md)\.
Have an Amazon S3 bucket in your AWS account\. To create one, see [How do I create an S3 Bucket?](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/create-bucket.html) in the *Amazon Simple Storage Service User Guide*\. 
Upload your input file to an Amazon S3 bucket\. For more information, see [How do I upload files and folders to an S3 bucket?](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/upload-objects.html) in the *Amazon Simple Storage Service User Guide*\.

## Adding parallel data \(Amazon Translate console\)<a name="customizing-translations-parallel-data-adding-console"></a>

To add parallel data by using the Amazon Translate console, use the **Parallel data** page:

1. Open the [Amazon Translate console](https://console.aws.amazon.com/translate/home)\.

1. In the navigation menu on the left, choose **Customization**, and choose **Parallel data**\.

1. On the **Parallel data** page, choose **Create parallel data**\. The console shows the **Create parallel data** page\.

1. Provide the following:  
**Name**  
A custom name for the parallel data resource\. You must assign a name that is unique in the account and region\.  
**Description \- *optional***  
A custom description\.  
**Parallel data location on S3**  
The location of the parallel data input file in Amazon S3\. To provide the location by navigating to the file in Amazon S3, choose **Select file**\.  
**File format**  
The format of the parallel data input file\. Supported formats are Translation Memory eXchange \(TMX\), comma\-separated values \(CSV\), and tab\-separated values \(TSV\)\.

1. Under **Encryption key**, choose an AWS KMS key to secure your parallel data\. These KMS keys are managed by AWS Key Management Service \(AWS KMS\)\. For more information about AWS KMS, see the [AWS Key Management Service Developer Guide](https://docs.aws.amazon.com/kms/latest/developerguide/)\.  
**Use AWS owned key**  
Use a KMS key that is owned and managed by Amazon Translate\. This is the default option and is used to encrypt your information if you don't choose another method\. For more information, see [AWS owned keys](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#aws-owned-cmk) in the *AWS Key Management Service Developer Guide*\.  
**Use key from current account**  
Use one of the KMS keys that you manage in AWS KMS in your AWS account\. If you choose this option, a menu provides a list of your KMS keys to choose from\. For more information, see [Customer managed keys](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#customer-cmk) in the *AWS Key Management Service Developer Guide*\.  
**Use key from different account**  
Use a KMS key that is managed in AWS KMS in a different AWS account\. If you choose this option, the console provides a field for you to enter the Amazon Resource Name \(ARN\) of the KMS key\.

   For more information about encryption keys, see the *[AWS Key Management Service Developer Guide](https://docs.aws.amazon.com/kms/latest/developerguide/)*\.

1. Choose **Create parallel data**\. 

   The console returns to the **Parallel data** page, where the import status is shown in a banner at the top of the page\. After a few minutes, your parallel data resource is shown in the table\. When the value in the **Status** column is **Active**, the parallel data is ready for you to use in a batch translation job\.

### Error file for troubleshooting<a name="customizing-translations-parallel-data-adding-console-error-file"></a>

If Amazon Translate generates any errors or warnings while processing your input file, the console provides an error file that you can download to review the error messages\. The contents of this file resemble the following example:

```
{
  "summary": {
    "record_error_count": 1,
    "record_skipped_count": 0
  },
  "messages": [
    {
      "content": "Number 1 TU element",
      "message": "Invalid TMX format. One tu element should contain exactly one tuv element with the source language code: en"
    }
  ]
}
```

## Adding parallel data \(AWS CLI\)<a name="customizing-translations-parallel-data-adding-cli"></a>

To add parallel data by using the AWS CLI, use the `create-parallel-data` command\.

**Example create\-parallel\-data command**  
The following example creates a parallel data object by importing a TSV file from Amazon S3:  

```
$ aws translate create-parallel-data \
> --name my-parallel-data \
> --parallel-data-config S3Uri=s3://input-bucket/parallel-data-file.tsv,Format=TSV
```
If the command succeeds, Amazon Translate responds with the status of the new parallel data object:  

```
{
    "Name": "my-parallel-data",
    "Status": "CREATING"
}
```
You can monitor the ongoing status of the parallel data by using the `get-parallel-data` command\. When the status is `ACTIVE`, the parallel data is ready for you to use in a batch translation job\. For an example of the `get-parallel-data` command, see [To view the details for a parallel data object](customizing-translations-parallel-data-managing.md#customizing-translations-parallel-data-managing-cli-get)\.

## Using your parallel data<a name="customizing-translations-parallel-data-adding-next"></a>

Now that you have created a parallel data resource, you can apply it to a batch translation job to customize the output\. To run a batch job, see [Running a batch translation job](async-start.md)\.