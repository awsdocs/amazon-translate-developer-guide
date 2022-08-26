# Monitoring and analyzing batch translation jobs<a name="async-monitor"></a>

You can use a job's ID to monitor its progress and get the Amazon S3 location of its output documents\. To monitor a specific job, use the [DescribeTextTranslationJob](https://docs.aws.amazon.com/translate/latest/APIReference/API_DescribeTextTranslationJob.html) operation\. You can also use the [ListTextTranslationJobs](https://docs.aws.amazon.com/translate/latest/APIReference/API_ListTextTranslationJobs.html) operation to retrieve information on all of the translation jobs in your account\. To restrict results to jobs that match a certain criteria, use the [ListTextTranslationJobs](https://docs.aws.amazon.com/translate/latest/APIReference/API_ListTextTranslationJobs.html) operation's `filter` parameter\. You can filter results by job name, job status, or the date and time that the job was submitted\. 

**Example describe\-text\-translation\-job command**  
The following example check's a job's status by using the AWS CLI to run the [DescribeTextTranslationJob](https://docs.aws.amazon.com/translate/latest/APIReference/API_DescribeTextTranslationJob.html) command:  

```
$ aws translate describe-text-translation-job --job-id 1c1838f470806ab9c3e0057f14717bed
```
This command returns the following output:  

```
{
  "TextTranslationJobProperties": {
    "InputDataConfig": {
      "ContentType": "text/plain",
      "S3Uri": "s3://input-bucket-name/folder"
    },
    "EndTime": 1576551359.483,
    "SourceLanguageCode": "en",
    "DataAccessRoleArn": "arn:aws:iam::012345678901:role/service-role/AmazonTranslateInputOutputAccess",
    "JobId": "1c1838f470806ab9c3e0057f14717bed",
    "TargetLanguageCodes": [
      "fr"
    ],
    "JobName": "batch-test",
    "SubmittedTime": 1576544017.357,
    "JobStatus": "COMPLETED",
    "Message": "Your job has completed successfully.",
    "JobDetails": {
      "InputDocumentsCount": 77,
      "DocumentsWithErrorsCount": 0,
      "TranslatedDocumentsCount": 77
    },
    "OutputDataConfig": {
      "S3Uri": "s3://bucket-name/output/012345678901-TranslateText-1c1838f470806ab9c3e0057f14717bed/"
    }
  }
}
```

You can stop a batch translation job while its status is `IN_PROGRESS` by using the [StopTextTranslationJob](https://docs.aws.amazon.com/translate/latest/APIReference/API_StopTextTranslationJob.html) operation\.

**Example stop\-text\-translation\-job command**  
The following example stops a batch translation with by using the AWS CLI to run the [StopTextTranslationJob](https://docs.aws.amazon.com/translate/latest/APIReference/API_StopTextTranslationJob.html) command:  

```
$ aws translate stop-text-translation-job --job-id 5236d36ce5192abdb3e2519f3ab8b065
```
This command returns the following output:  

```
{
  "TextTranslationJobProperties": {
    "InputDataConfig": {
      "ContentType": "text/plain",
      "S3Uri": "s3://input-bucket-name/folder"
    },
    "SourceLanguageCode": "en",
    "DataAccessRoleArn": "arn:aws:iam::012345678901:role/service-role/AmazonTranslateInputOutputAccess",
    "TargetLanguageCodes": [
      "fr"
    ],
    "JobName": "canceled-test",
    "SubmittedTime": 1576558958.167,
    "JobStatus": "STOP_REQUESTED",
    "JobId": "5236d36ce5192abdb3e2519f3ab8b065",
    "OutputDataConfig": {
      "S3Uri": "s3://output-bucket-name/012345678901-TranslateText-5236d36ce5192abdb3e2519f3ab8b065/"
    }
  }
}
```