# Encryption at Rest<a name="encryption-at-rest"></a>

For the batch translation jobs that you run with Amazon Translate, your translation input and output are both encrypted at rest\. However, the encryption method is different for each\.

Amazon Translate also uses an Amazon Elastic Block Store \(Amazon EBS\) volume encrypted with the default key\.



## Translation Input<a name="encryption-at-rest-input"></a>

When you use Amazon Translate to translate documents in batch, you store a set of input documents in an Amazon S3 bucket\. To encrypt these documents at rest, you can use the SSE\-S3 server\-side encryption option that is provided by Amazon S3\. With this option, each object is encrypted with a unique key that is managed by Amazon S3\. 

For more information, see [Protecting data using server\-side encryption with Amazon S3\-managed encryption keys \(SSE\-S3\)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Console User Guide*\.

## Translation Output<a name="encryption-at-rest-output"></a>

When Amazon Translate completes a batch translation job, it puts the output in an Amazon S3 bucket in your AWS account\. To encrypt the output at rest, Amazon Translate uses the SSE\-KMS encryption option that is provided by Amazon S3\. With this option, your output is encrypted with a customer master key \(CMK\) that is stored in AWS Key Management Service \(AWS KMS\)\. 

For this encryption, Amazon Translate uses an *AWS managed CMK*\. This type of CMK is created by AWS and stored in AWS KMS in your account\. However, you cannot manage this CMK yourself\. It is managed and used on your behalf only by AWS\.

For more information about SSE\-KMS, see [Protecting Data Using Server\-Side Encryption with CMKs Stored in AWS Key Management Service \(SSE\-KMS\)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingKMSEncryption.html) in the *Amazon Simple Storage Service Console User Guide*\.

For more information about CMKs, see [Customer master keys \(CMKs\)](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#master_keys) in the *AWS Key Management Service Developer Guide*\.