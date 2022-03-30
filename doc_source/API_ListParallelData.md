# ListParallelData<a name="API_ListParallelData"></a>

Provides a list of your parallel data resources in Amazon Translate\.

## Request Syntax<a name="API_ListParallelData_RequestSyntax"></a>

```
{
   "MaxResults": number,
   "NextToken": "string"
}
```

## Request Parameters<a name="API_ListParallelData_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [MaxResults](#API_ListParallelData_RequestSyntax) **   <a name="Translate-ListParallelData-request-MaxResults"></a>
The maximum number of parallel data resources returned for each request\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_ListParallelData_RequestSyntax) **   <a name="Translate-ListParallelData-request-NextToken"></a>
A string that specifies the next page of results to return in a paginated response\.  
Type: String  
Length Constraints: Maximum length of 8192\.  
Pattern: `\p{ASCII}{0,8192}`   
Required: No

## Response Syntax<a name="API_ListParallelData_ResponseSyntax"></a>

```
{
   "NextToken": "string",
   "ParallelDataPropertiesList": [ 
      { 
         "Arn": "string",
         "CreatedAt": number,
         "Description": "string",
         "EncryptionKey": { 
            "Id": "string",
            "Type": "string"
         },
         "FailedRecordCount": number,
         "ImportedDataSize": number,
         "ImportedRecordCount": number,
         "LastUpdatedAt": number,
         "LatestUpdateAttemptAt": number,
         "LatestUpdateAttemptStatus": "string",
         "Message": "string",
         "Name": "string",
         "ParallelDataConfig": { 
            "Format": "string",
            "S3Uri": "string"
         },
         "SkippedRecordCount": number,
         "SourceLanguageCode": "string",
         "Status": "string",
         "TargetLanguageCodes": [ "string" ]
      }
   ]
}
```

## Response Elements<a name="API_ListParallelData_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [NextToken](#API_ListParallelData_ResponseSyntax) **   <a name="Translate-ListParallelData-response-NextToken"></a>
The string to use in a subsequent request to get the next page of results in a paginated response\. This value is null if there are no additional pages\.  
Type: String  
Length Constraints: Maximum length of 8192\.  
Pattern: `\p{ASCII}{0,8192}` 

 ** [ParallelDataPropertiesList](#API_ListParallelData_ResponseSyntax) **   <a name="Translate-ListParallelData-response-ParallelDataPropertiesList"></a>
The properties of the parallel data resources returned by this request\.  
Type: Array of [ParallelDataProperties](API_ParallelDataProperties.md) objects

## Errors<a name="API_ListParallelData_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidParameterValueException **   
The value of the parameter is not valid\. Review the value of the parameter you are using to correct it, and then retry your operation\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\.  
HTTP Status Code: 400

## See Also<a name="API_ListParallelData_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/translate-2017-07-01/ListParallelData) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/translate-2017-07-01/ListParallelData) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/ListParallelData) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/ListParallelData) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/ListParallelData) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/translate-2017-07-01/ListParallelData) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/translate-2017-07-01/ListParallelData) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/translate-2017-07-01/ListParallelData) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/ListParallelData) 