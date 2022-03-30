# StartTextTranslationJob<a name="API_StartTextTranslationJob"></a>

Starts an asynchronous batch translation job\. Batch translation jobs can be used to translate large volumes of text across multiple documents at once\. For more information, see [Asynchronous batch processing with Amazon Translate](async.md)\.

Batch translation jobs can be described with the [DescribeTextTranslationJob](API_DescribeTextTranslationJob.md) operation, listed with the [ListTextTranslationJobs](API_ListTextTranslationJobs.md) operation, and stopped with the [StopTextTranslationJob](API_StopTextTranslationJob.md) operation\.

**Note**  
Amazon Translate does not support batch translation of multiple source languages at once\.

## Request Syntax<a name="API_StartTextTranslationJob_RequestSyntax"></a>

```
{
   "ClientToken": "string",
   "DataAccessRoleArn": "string",
   "InputDataConfig": { 
      "ContentType": "string",
      "S3Uri": "string"
   },
   "JobName": "string",
   "OutputDataConfig": { 
      "EncryptionKey": { 
         "Id": "string",
         "Type": "string"
      },
      "S3Uri": "string"
   },
   "ParallelDataNames": [ "string" ],
   "Settings": { 
      "Formality": "string",
      "Profanity": "string"
   },
   "SourceLanguageCode": "string",
   "TargetLanguageCodes": [ "string" ],
   "TerminologyNames": [ "string" ]
}
```

## Request Parameters<a name="API_StartTextTranslationJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientToken](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-ClientToken"></a>
A unique identifier for the request\. This token is generated for you when using the Amazon Translate SDK\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: Yes

 ** [DataAccessRoleArn](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of an AWS Identity Access and Management \(IAM\) role that grants Amazon Translate read access to your input data\. For more information, see [Identity and access management for Amazon Translate](identity-and-access-management.md)\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [InputDataConfig](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-InputDataConfig"></a>
Specifies the format and location of the input documents for the translation job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: Yes

 ** [JobName](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-JobName"></a>
The name of the batch translation job to be performed\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** [OutputDataConfig](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-OutputDataConfig"></a>
Specifies the S3 folder to which your job output will be saved\.   
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: Yes

 ** [ParallelDataNames](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-ParallelDataNames"></a>
The name of a parallel data resource to add to the translation job\. This resource consists of examples that show how you want segments of text to be translated\. When you add parallel data to a translation job, you create an *Active Custom Translation* job\.   
This parameter accepts only one parallel data resource\.  
Active Custom Translation jobs are priced at a higher rate than other jobs that don't use parallel data\. For more information, see [Amazon Translate pricing](http://aws.amazon.com/translate/pricing/)\.
For a list of available parallel data resources, use the [ListParallelData](API_ListParallelData.md) operation\.  
For more information, see [Customizing your translations with parallel data \(Active Custom Translation\)](customizing-translations-parallel-data.md)\.  
Type: Array of strings  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$`   
Required: No

 ** [Settings](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-Settings"></a>
Settings to configure your translation output, including the option to mask profane words and phrases\. `StartTextTranslationJob` does not support the formality setting\.  
Type: [TranslationSettings](API_TranslationSettings.md) object  
Required: No

 ** [SourceLanguageCode](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-SourceLanguageCode"></a>
The language code of the input language\. For a list of language codes, see [Supported languages and language codes](what-is.md#what-is-languages)\.  
Amazon Translate does not automatically detect a source language during batch translation jobs\.  
Type: String  
Length Constraints: Minimum length of 2\. Maximum length of 5\.  
Required: Yes

 ** [TargetLanguageCodes](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-TargetLanguageCodes"></a>
The language code of the output language\.  
Type: Array of strings  
Array Members: Fixed number of 1 item\.  
Length Constraints: Minimum length of 2\. Maximum length of 5\.  
Required: Yes

 ** [TerminologyNames](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-TerminologyNames"></a>
The name of a custom terminology resource to add to the translation job\. This resource lists examples source terms and the desired translation for each term\.  
This parameter accepts only one custom terminology resource\.  
For a list of available custom terminology resources, use the [ListTerminologies](API_ListTerminologies.md) operation\.  
For more information, see [Customizing your translations with custom terminology](how-custom-terminology.md)\.  
Type: Array of strings  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$`   
Required: No

## Response Syntax<a name="API_StartTextTranslationJob_ResponseSyntax"></a>

```
{
   "JobId": "string",
   "JobStatus": "string"
}
```

## Response Elements<a name="API_StartTextTranslationJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [JobId](#API_StartTextTranslationJob_ResponseSyntax) **   <a name="Translate-StartTextTranslationJob-response-JobId"></a>
The identifier generated for the job\. To get the status of a job, use this ID with the [DescribeTextTranslationJob](API_DescribeTextTranslationJob.md) operation\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$` 

 ** [JobStatus](#API_StartTextTranslationJob_ResponseSyntax) **   <a name="Translate-StartTextTranslationJob-response-JobStatus"></a>
The status of the job\. Possible values include:  
+  `SUBMITTED` \- The job has been received and is queued for processing\.
+  `IN_PROGRESS` \- Amazon Translate is processing the job\.
+  `COMPLETED` \- The job was successfully completed and the output is available\.
+  `COMPLETED_WITH_ERROR` \- The job was completed with errors\. The errors can be analyzed in the job's output\.
+  `FAILED` \- The job did not complete\. To get details, use the [DescribeTextTranslationJob](API_DescribeTextTranslationJob.md) operation\.
+  `STOP_REQUESTED` \- The user who started the job has requested that it be stopped\.
+  `STOPPED` \- The job has been stopped\.
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | COMPLETED_WITH_ERROR | FAILED | STOP_REQUESTED | STOPPED` 

## Errors<a name="API_StartTextTranslationJob_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidParameterValueException **   
The value of the parameter is not valid\. Review the value of the parameter you are using to correct it, and then retry your operation\.  
HTTP Status Code: 400

 ** InvalidRequestException **   
 The request that you made is not valid\. Check your request to determine why it's not valid and then retry the request\.   
HTTP Status Code: 400

 ** ResourceNotFoundException **   
The resource you are looking for has not been found\. Review the resource you're looking for and see if a different resource will accomplish your needs before retrying the revised request\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\.  
HTTP Status Code: 400

 ** UnsupportedLanguagePairException **   
Amazon Translate does not support translation from the language of the source text into the requested target language\. For more information, see [Exception handling](how-it-works.md#how-to-error-msg)\.   
HTTP Status Code: 400

## See Also<a name="API_StartTextTranslationJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/StartTextTranslationJob) 