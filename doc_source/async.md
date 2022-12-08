# Asynchronous batch processing with Amazon Translate<a name="async"></a>

To translate large collections of documents \(up to 5 GB in size\), use the Amazon Translate asynchronous batch processing operation, [StartTextTranslationJob](https://docs.aws.amazon.com/translate/latest/APIReference/API_StartTextTranslationJob.html)\. This is best for collections of short documents, such as social media postings or user reviews, or any situation in which instantaneous translation is not required\.

To perform an asynchronous batch translation, you typically perform the following steps:

1. Store a set of documents in an input folder inside of an Amazon S3 bucket\.

1. Start a batch translation job\.

1. As part of your request, provide Amazon Translate with an IAM role that has read access to the input Amazon S3 folder and all its sub\-folders\. The role must also have read and write access to an output Amazon S3 bucket\.

1. Monitor the progress of the batch translation job\.

1. Retrieve the results of the batch translation job from the specified output bucket\.

## Region availability<a name="async-regions"></a>

Batch translation is supported in the following AWS Regions:
+ US East \(N\. Virginia\)
+ US East \(Ohio\)
+ US West \(Oregon\)
+ Asia Pacific \(Seoul\)
+ Europe \(Frankfurt\)
+ Europe \(Ireland\)
+ Europe \(London\)

**Topics**