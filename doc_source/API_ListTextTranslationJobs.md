# ListTextTranslationJobs<a name="API_ListTextTranslationJobs"></a>

Gets a list of the batch translation jobs that you have submitted\.

## Request Syntax<a name="API_ListTextTranslationJobs_RequestSyntax"></a>

```
{
   "Filter": { 
      "JobName": "string",
      "JobStatus": "string",
      "SubmittedAfterTime": number,
      "SubmittedBeforeTime": number
   },
   "MaxResults": number,
   "NextToken": "string"
}
```

## Request Parameters<a name="API_ListTextTranslationJobs_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Filter](#API_ListTextTranslationJobs_RequestSyntax) **   <a name="Translate-ListTextTranslationJobs-request-Filter"></a>
The parameters that specify which batch translation jobs to retrieve\. Filters include job name, job status, and submission time\. You can only set one filter at a time\.  
Type: [TextTranslationJobFilter](API_TextTranslationJobFilter.md) object  
Required: No

 ** [MaxResults](#API_ListTextTranslationJobs_RequestSyntax) **   <a name="Translate-ListTextTranslationJobs-request-MaxResults"></a>
The maximum number of results to return in each page\. The default value is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_ListTextTranslationJobs_RequestSyntax) **   <a name="Translate-ListTextTranslationJobs-request-NextToken"></a>
The token to request the next page of results\.  
Type: String  
Length Constraints: Maximum length of 8192\.  
Pattern: `\p{ASCII}{0,8192}`   
Required: No

## Response Syntax<a name="API_ListTextTranslationJobs_ResponseSyntax"></a>

```
{
   "NextToken": "string",
   "TextTranslationJobPropertiesList": [ 
      { 
         "DataAccessRoleArn": "string",
         "EndTime": number,
         "InputDataConfig": { 
            "ContentType": "string",
            "S3Uri": "string"
         },
         "JobDetails": { 
            "DocumentsWithErrorsCount": number,
            "InputDocumentsCount": number,
            "TranslatedDocumentsCount": number
         },
         "JobId": "string",
         "JobName": "string",
         "JobStatus": "string",
         "Message": "string",
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
         "SubmittedTime": number,
         "TargetLanguageCodes": [ "string" ],
         "TerminologyNames": [ "string" ]
      }
   ]
}
```

## Response Elements<a name="API_ListTextTranslationJobs_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [NextToken](#API_ListTextTranslationJobs_ResponseSyntax) **   <a name="Translate-ListTextTranslationJobs-response-NextToken"></a>
The token to use to retrieve the next page of results\. This value is `null` when there are no more results to return\.  
Type: String  
Length Constraints: Maximum length of 8192\.  
Pattern: `\p{ASCII}{0,8192}` 

 ** [TextTranslationJobPropertiesList](#API_ListTextTranslationJobs_ResponseSyntax) **   <a name="Translate-ListTextTranslationJobs-response-TextTranslationJobPropertiesList"></a>
A list containing the properties of each job that is returned\.  
Type: Array of [TextTranslationJobProperties](API_TextTranslationJobProperties.md) objects

## Errors<a name="API_ListTextTranslationJobs_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidFilterException **   
The filter specified for the operation is not valid\. Specify a different filter\.  
HTTP Status Code: 400

 ** InvalidRequestException **   
 The request that you made is not valid\. Check your request to determine why it's not valid and then retry the request\.   
HTTP Status Code: 400

 ** TooManyRequestsException **   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\.  
HTTP Status Code: 400

## See Also<a name="API_ListTextTranslationJobs_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/translate-2017-07-01/ListTextTranslationJobs) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/translate-2017-07-01/ListTextTranslationJobs) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/ListTextTranslationJobs) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/ListTextTranslationJobs) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/ListTextTranslationJobs) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/translate-2017-07-01/ListTextTranslationJobs) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/translate-2017-07-01/ListTextTranslationJobs) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/translate-2017-07-01/ListTextTranslationJobs) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/ListTextTranslationJobs) 