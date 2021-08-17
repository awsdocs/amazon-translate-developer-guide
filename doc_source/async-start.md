# Running a Batch Translation Job<a name="async-start"></a>

You can run a batch translation job by using the Amazon Translate console, the AWS CLI, or the Amazon Translate API\.

**Notes**  
Batch translation jobs are long\-running operations and can take significant time to complete\. For example, batch translation on a small dataset might take a few minutes, while very large datasets may take up to 2 days or more\. Completion time is also dependent on the availability of resources\.
Amazon Translate does not automatically detect a source language during batch translation jobs\.

## Running a Batch Translation Job \(Amazon Translate Console\)<a name="async-start-console"></a>

To run a translation job by using the Amazon Translate console, use the **Batch translation** page to create the job:

1. Open the Amazon Translate console at [https://console\.aws\.amazon\.com/translate/](https://console.aws.amazon.com/translate/)

1. In the navigation menu on the left, choose **Batch translation**\.

1. On the **Translation jobs** page, choose **Create job**\. The console shows the **Create translation job** page\.

1. Enter the following:  
**Name**  
A custom name for the batch translation job\.  
**Source language**  
The language of the source files that are being translated\.  
**Target language**  
The language that your files are translated into\.  
**Input S3 location**  
The input folder that contains the translation source files in Amazon S3\. To provide the folder by navigating to it in Amazon S3, choose **Select folder**\.  
**File format**  
The format of the translation source files\.  
**Output S3 location**  
The output folder in Amazon S3 where Amazon Translate puts the translation output\. To provide the folder by navigating to it in Amazon S3, choose **Select folder**\.

1. Under **Customization \- optional**, you can choose to customize the output of your translation job with the following resources:  
**Custom terminology**  
Consists of examples of source terms and their target translations\. By using custom terminology, you can ensure that your brand names, character names, model names, and other unique content is translated exactly the way you need it, regardless of its context\.  
For more information, see [Customizing Your Translations with Custom Terminology](how-custom-terminology.md)\.  
**Parallel data**  
Consists of examples that show how you want segments of text to be translated\. When you add parallel data to a batch translation job, you create an *Active Custom Translation* job\. By adding parallel data, you can influence your translations for terms or phrases that are unique to a specific domain, such as law or finance\. You can also influence the style or tone of your translations\.  
Active Custom Translation jobs are priced at a higher rate than other jobs that don't use parallel data\. For more information, see [Amazon Translate pricing](http://aws.amazon.com/translate/pricing/)\.
For more information, see [Customizing Your Translations with Parallel Data \(Active Custom Translation\)](customizing-translations-parallel-data.md)\.

1. Under **Access permissions**, provide Amazon Translate with an IAM role that grants the required permissions to your input and output files in Amazon S3:
   + If you already have this IAM role in your account, choose **Use an existing IAM role**, and select it under **IAM role**\.
   + If you don't already have this IAM role in your account, choose **Create an IAM role**\. For **IAM role**, choose **Input and output S3 buckets**\. For **Role name**, provide a custom name\. When you create the translation job, Amazon Translate creates the role automatically\. The role name in IAM is prefixed with *AmazonTranslateServiceRole\-*\.

1. Choose **Create job**\.

   The console returns to the **Translation jobs** page, where the job creation status is shown in a banner at the top of the page\. After a few minutes, your job is shown in the table\.

1. Choose the job name in the **Name** column to open the job details page\.

   While your translation job runs, the **Status** field shows **In progress**\. 

1. When the status becomes **Completed**, go to your translation output by choosing the link under **Output file location**\. The console goes to your output bucket in Amazon S3\.

1. To download your output files, select the checkbox for each, and choose **Download**\.

## Running a Batch Translation Job \(AWS CLI\)<a name="async-start-cli"></a>

To run a translation job by using the AWS CLI, use the [https://docs.aws.amazon.com/cli/latest/reference/translate/start-text-translation-job.html](https://docs.aws.amazon.com/cli/latest/reference/translate/start-text-translation-job.html) command, and specify the name of your parallel data resource for the `parallel-data-names` parameter\.

**Example start\-text\-translation\-job command**  
The following example runs a translation job by submitting an Excel file that is stored in an input bucket in Amazon S3\. This job is customized by the parallel data that is included in the request\.  

```
$ aws translate start-text-translation-job \
> --input-data-config ContentType=application/vnd.openxmlformats-officedocument.spreadsheetml.sheet,S3Uri=s3://my-s3-bucket/input/ \
> --output-data-config S3Uri=s3://my-s3-bucket/output/ \
> --data-access-role-arn arn:aws:iam::111122223333:role/my-iam-role \
> --source-language-code=en --target-language-codes=es \
> --job-name my-translation-job
```
If the command succeeds, Amazon Translate responds with the job ID and status:  

```
{
    "JobId": "4446f95f20c88a4b347449d3671fbe3d",
    "JobStatus": "SUBMITTED"
}
```
If you want to customize the output of your translation job, you can use the following parameters:    
`--terminology-names`  
Provides one or more custom terminology resources\. These consist of examples of source terms and their target translations\. By using custom terminology, you can ensure that your brand names, character names, model names, and other unique content is translated exactly the way you need it, regardless of its context\.  
For more information, see [Customizing Your Translations with Custom Terminology](how-custom-terminology.md)\.  
`--parallel-data-names`  
Provides one or more parallel data resources\. These consist of examples that show how you want segments of text to be translated\. When you add parallel data to a batch translation job, you create an *Active Custom Translation* job\. By adding parallel data, you can influence your translations for terms or phrases that are unique to a specific domain, such as law or finance\. You can also influence the style or tone of your translations\.  
Active Custom Translation jobs are priced at a higher rate than other jobs that don't use parallel data\. For more information, see [Amazon Translate pricing](http://aws.amazon.com/translate/pricing/)\.
For more information, see [Customizing Your Translations with Parallel Data \(Active Custom Translation\)](customizing-translations-parallel-data.md)\.

To check the status of your translation job, use the [https://docs.aws.amazon.com/cli/latest/reference/translate/describe-text-translation-job.html](https://docs.aws.amazon.com/cli/latest/reference/translate/describe-text-translation-job.html) command\.

**Example describe\-text\-translation\-job command**  

The following example checks the job status by providing the job ID\. This ID was provided by Amazon Translate when the job was initiated by the `start-text-translation-job` command\.

```
$ aws translate describe-text-translation-job \
> --job-id 4446f95f20c88a4b347449d3671fbe3d
```

Amazon Translate responds with the job properties, which include its status:

```
{
    "TextTranslationJobProperties": {
        "JobId": "4446f95f20c88a4b347449d3671fbe3d",
        "JobName": "my-translation-job",
        "JobStatus": "COMPLETED",
        "JobDetails": {
            "TranslatedDocumentsCount": 0,
            "DocumentsWithErrorsCount": 0,
            "InputDocumentsCount": 1
        },
        "SourceLanguageCode": "en",
        "TargetLanguageCodes": [
            "es"
        ],
        "SubmittedTime": 1598661012.468,
        "InputDataConfig": {
            "S3Uri": "s3://my-s3-bucket/input/",
            "ContentType": "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"
        },
        "OutputDataConfig": {
            "S3Uri": "s3://my-s3-bucket/output/111122223333-TranslateText-4446f95f20c88a4b347449d3671fbe3d/"
        },
        "DataAccessRoleArn": "arn:aws:iam::111122223333:role/my-iam-role"
    }
}
```

If the `JobStatus` value is `IN_PROGRESS`, allow a few minutes to pass, and run `describe-text-translation-job`[https://docs.aws.amazon.com/cli/latest/reference/translate/describe-text-translation-job.html](https://docs.aws.amazon.com/cli/latest/reference/translate/describe-text-translation-job.html) again until the status is `COMPLETED`\. When the job completes, you can download the translation results at the location provided by the `S3Uri` field under `OutputDataConfig`\.

## Running a Batch Translation Job \(Amazon Translate API\)<a name="async-start-api"></a>

To submit a batch translation job by using the Amazon Translate API, use the [StartTextTranslationJob](API_StartTextTranslationJob.md) operation\.