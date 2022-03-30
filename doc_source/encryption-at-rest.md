# Encryption at rest<a name="encryption-at-rest"></a>

For the batch translation jobs that you run with Amazon Translate, your translation input and output are both encrypted at rest\. However, the encryption method is different for each\.

Amazon Translate also uses an Amazon Elastic Block Store \(Amazon EBS\) volume encrypted with the default key\.

## Translation input<a name="encryption-at-rest-input"></a>

When you use Amazon Translate to translate documents in batch, you store a set of input documents in an Amazon S3 bucket\. To encrypt these documents at rest, you can use the SSE\-S3 server\-side encryption option that is provided by Amazon S3\. With this option, each object is encrypted with a unique key that is managed by Amazon S3\. 

For more information, see [Protecting data using server\-side encryption with Amazon S3\-managed encryption keys \(SSE\-S3\)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service User Guide*\.

## Translation output<a name="encryption-at-rest-output"></a>

When Amazon Translate completes a batch translation job, it puts the output in an Amazon S3 bucket in your AWS account\. To encrypt the output at rest, Amazon Translate uses the SSE\-KMS encryption option that is provided by Amazon S3\. With this option, your output is encrypted with a key that is stored in AWS Key Management Service \(AWS KMS\)\. 

For more information about SSE\-KMS, see [Protecting Data using server\-side encryption with AWS Key Management Service \(SSE\-KMS\)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingKMSEncryption.html) in the *Amazon Simple Storage Service User Guide*\.

For more information about KMS keys, see [AWS KMS keys](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#kms_keys) in the *AWS Key Management Service Developer Guide*\.

For this encryption, Amazon Translate can use either of the following types of keys:

**AWS managed key**  
By default, Amazon Translate uses an *AWS managed key*\. This type of KMS key is created by AWS and stored in your account\. However, you cannot manage this KMS key yourself\. It is managed and used on your behalf only by AWS\.

**Customer managed key**  
Optionally, you can choose to encrypt your output with a *customer managed key*, which is a KMS key that you create, own, and manage in your AWS account\.  
Before you can use your own KMS key, you must add permissions to the IAM service role that Amazon Translate uses to access your output bucket in Amazon S3\. If you want to use a KMS key that's in a different AWS account, you must also update the key policy in AWS KMS\. For more information, see [Prerequisite permissions to customize encryption](async-prereqs.md#async-prereqs-permissions-custom-encryption)\.  
You can choose to use your customer managed key when you run a batch translation job\. For more information, see [Running a batch translation job](async-start.md)\.