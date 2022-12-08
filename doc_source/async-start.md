# Running a batch translation job<a name="async-start"></a>

You can run a batch translation job by using the Amazon Translate console, the AWS CLI, or the Amazon Translate API\.

**Note**  
Batch translation jobs are long\-running operations and can take significant time to complete\. For example, batch translation on a small dataset might take a few minutes, while very large datasets may take up to 2 days or more\. Completion time is also dependent on the availability of resources\. 

## Amazon Translate console<a name="async-start-console"></a>

To run a translation job by using the Amazon Translate console, use the **Batch translation** page to create the job:

1. Open the [Amazon Translate console](https://console.aws.amazon.com/translate/home)\.

1. In the navigation menu on the left, choose **Batch translation**\.

1. On the **Translation jobs** page, choose **Create job**\. The console shows the **Create translation job** page\.

1. Under **Job settings**, do the following:

   1. For **Name**, enter a custom name for the batch translation job\.

   1. For **Source language**, select the language of the source files\. If you don't know the language of the source files, or your input documents contains different source languages, select `auto`\. Amazon Translate auto detects the source language for each file\. 

   1. For **Target languages**, select up to 10 languages\. Amazon Translate translates each source file into each target language\.

1. Under **Input data**, do the following:

   1. For **Input S3 location**, specify the input folder that contains the translation source files in Amazon S3\. To provide the folder by navigating to it in Amazon S3, choose **Select folder**\.

   1. For **File format**, select format of the translation source files\.

1. Under **Output data**, do the following:

   1. For **Output S3 location**, specify the output folder in Amazon S3 where Amazon Translate puts the translation output\. To provide the folder by navigating to it in Amazon S3, choose **Select folder**\.

   1. Optionally, choose **Customize encryption settings \(advanced\)** if you want to encrypt your output with a customer managed key that you manage in the AWS Key Management Service \(AWS KMS\)\.

      By default, Amazon Translate encrypts your translation output using a KMS key that is created, managed, and used on your behalf by AWS\. Choose this option if you want to encrypt your output with your own KMS key instead\. 

      If you want to use a KMS key from the current AWS account, select it under **Choose an AWS Key Management Service key**\. Or, if you want to use a KMS key from a different AWS account, enter the Amazon Resource Name \(ARN\) for that key\.
**Note**  
Before you can use your own KMS key, you must add permissions to the service role for Amazon Translate in IAM\. If you want to use a KMS key from a different account, you must also update the key policy in AWS KMS\. For more information, see [Prerequisite permissions to customize encryption](async-prereqs.md#async-prereqs-permissions-custom-encryption)\.

1. Under **Customizations \- optional**, you can choose to customize the output of your translation job with the following settings:  
**Profanity**  
Masks profane words and phrases in your translation output\. If you specify multiple target languages for the job, all the target languages must support profanity masking\. If any of the target languages don't support profanity masking, the translation job won't mask profanity for any target language\.  
For more information, see [Masking profane words and phrases in Amazon Translate](customizing-translations-profanity.md)\.  
**Formality**  
For some target languages, you can set **Formality** to formal or informal\. If you specify multiple target languages for the job, translate ignores the formality setting for any unsupported target language\.  
 For more information, see [Setting formality in Amazon Translate](customizing-translations-formality.md)\.  
**Custom terminology**  
Consists of example source terms and the desired translation for each term\. If you specify multiple target languages for the job, translate uses the designated terminology for each requested target language that has an entry for the source term in the terminology file\.  
For more information, see [Customizing your translations with custom terminology](how-custom-terminology.md)\.  
**Parallel data**  
Consists of examples that show how you want segments of text to be translated\. If you specify multiple target languages for the job, the parallel data file must include translations for all the target languages\.  
When you add parallel data to a batch translation job, you create an *Active Custom Translation* job\.  
Active Custom Translation jobs are priced at a higher rate than other jobs that don't use parallel data\. For more information, see [Amazon Translate pricing](http://aws.amazon.com/translate/pricing/)\.
For more information, see [Customizing your translations with parallel data \(Active Custom Translation\)](customizing-translations-parallel-data.md)\.

1. Under **Access permissions**, provide Amazon Translate with an IAM role that grants the required permissions to your input and output files in Amazon S3:
   + If you already have this IAM role in your account, choose **Use an existing IAM role**, and select it under **IAM role**\.
   + If you don't already have this IAM role in your account, choose **Create an IAM role**\. For **IAM role**, choose **Input and output S3 buckets**\. For **Role name**, provide a custom name\. When you create the translation job, Amazon Translate creates the role automatically\. The role name in IAM is prefixed with *AmazonTranslateServiceRole\-*\.
**Note**  
If you chose to encrypt your translation output with your own KMS key, then you cannot choose **Create an IAM role**\. In this case, you must use a preexisting IAM role, and your KMS key must have a key policy that allows the role to use the key\.   
For more information, see [Prerequisite permissions to customize encryption](async-prereqs.md#async-prereqs-permissions-custom-encryption)

1. Choose **Create job**\.

   The console returns to the **Translation jobs** page, where the job creation status is shown in a banner at the top of the page\. After a few minutes, your job is shown in the table\.

1. Choose the job name in the **Name** column to open the job details page\.

   While your translation job runs, the **Status** field shows **In progress**\. 

1. When the status becomes **Completed**, go to your translation output by choosing the link under **Output file location**\. The console goes to your output bucket in Amazon S3\.

1. To download your output files, select the check box for each, and choose **Download**\.

## AWS CLI<a name="async-start-cli"></a>

To run a translation job by using the AWS CLI, use the [https://docs.aws.amazon.com/cli/latest/reference/translate/start-text-translation-job.html](https://docs.aws.amazon.com/cli/latest/reference/translate/start-text-translation-job.html) command, and specify the name of your parallel data resource for the `parallel-data-names` parameter\.

**Example Start\-text\-translation\-job command**  
The following example runs a translation job by submitting an Excel file that is stored in an input bucket in Amazon S3\. This job is customized by the parallel data that is included in the request\.  

```
$ aws translate start-text-translation-job \
> --input-data-config ContentType=application/vnd.openxmlformats-officedocument.spreadsheetml.sheet,S3Uri=s3://my-s3-bucket/input/ \
> --output-data-config S3Uri=s3://my-s3-bucket/output/ \
> --data-access-role-arn arn:aws:iam::111122223333:role/my-iam-role \
> --source-language-code en \
> --target-language-codes es it \
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
`--settings`  
Settings to configure your translation output, including the following options:  
Enable profanity to mask profane words and phrases\. To enable, set the profanity parameter to `Profanity=MASK`\. For more information, see [Masking profane words and phrases in Amazon Translate](customizing-translations-profanity.md)\. If any of the target languages don't support profanity masking, the translation job won't mask profanity for any target language\.  
Set the level of formality in the translation output\. Set the `Formality` parameter to `FORMAL` or `INFORMAL`\. If you specify multiple target languages for the job, translate ignores the formality setting for any unsupported target language\. For more information, see [Setting formality in Amazon Translate](customizing-translations-formality.md)\.  
`--terminology-names`  
The name of a custom terminology resource to add to the translation job\. This resource lists example source terms and the desired translation for each term\. If you specify multiple target languages for the job, translate uses the designated terminology for each requested target language that has an entry for the source term in the terminology file\.  
This parameter accepts only one custom terminology resource\.  
For a list of available custom terminology resources, use the [https://docs.aws.amazon.com/cli/latest/reference/translate/list-terminologies.html](https://docs.aws.amazon.com/cli/latest/reference/translate/list-terminologies.html) command\.  
For more information, see [Customizing your translations with custom terminology](how-custom-terminology.md)\.  
`--parallel-data-names`  
The name of a parallel data resource to add to the translation job\. This resource consists of examples that show how you want segments of text to be translated\. If you specify multiple target languages for the job, the parallel data file must include translations for all the target languages\.  
When you add parallel data to a translation job, you create an *Active Custom Translation* job\.  
This parameter accepts only one parallel data resource\.  
Active Custom Translation jobs are priced at a higher rate than other jobs that don't use parallel data\. For more information, see [Amazon Translate pricing](http://aws.amazon.com/translate/pricing/)\.
For a list of available parallel data resources, use the [https://docs.aws.amazon.com/cli/latest/reference/translate/list-parallel-data.html](https://docs.aws.amazon.com/cli/latest/reference/translate/list-parallel-data.html) command\.  
For more information, see [Customizing your translations with parallel data \(Active Custom Translation\)](customizing-translations-parallel-data.md)\.

To check the status of your translation job, use the [https://docs.aws.amazon.com/cli/latest/reference/translate/describe-text-translation-job.html](https://docs.aws.amazon.com/cli/latest/reference/translate/describe-text-translation-job.html) command\.

**Example Describe\-text\-translation\-job command**  

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
            "es", 
            "it" 
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

If the `JobStatus` value is `IN_PROGRESS`, allow a few minutes to pass, and run [https://docs.aws.amazon.com/cli/latest/reference/translate/describe-text-translation-job.html](https://docs.aws.amazon.com/cli/latest/reference/translate/describe-text-translation-job.html) again until the status is `COMPLETED`\. When the job completes, you can download the translation results at the location provided by the `S3Uri` field under `OutputDataConfig`\.

## Amazon Translate API<a name="async-start-api"></a>

To submit a batch translation job by using the Amazon Translate API, use the [StartTextTranslationJob](https://docs.aws.amazon.com/translate/latest/APIReference/API_StartTextTranslationJob.html) operation\.