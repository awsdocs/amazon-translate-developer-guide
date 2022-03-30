# UpdateParallelData<a name="API_UpdateParallelData"></a>

Updates a previously created parallel data resource by importing a new input file from Amazon S3\.

## Request Syntax<a name="API_UpdateParallelData_RequestSyntax"></a>

```
{
   "ClientToken": "string",
   "Description": "string",
   "Name": "string",
   "ParallelDataConfig": { 
      "Format": "string",
      "S3Uri": "string"
   }
}
```

## Request Parameters<a name="API_UpdateParallelData_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientToken](#API_UpdateParallelData_RequestSyntax) **   <a name="Translate-UpdateParallelData-request-ClientToken"></a>
A unique identifier for the request\. This token is automatically generated when you use Amazon Translate through an AWS SDK\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: Yes

 ** [Description](#API_UpdateParallelData_RequestSyntax) **   <a name="Translate-UpdateParallelData-request-Description"></a>
A custom description for the parallel data resource in Amazon Translate\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `[\P{M}\p{M}]{0,256}`   
Required: No

 ** [Name](#API_UpdateParallelData_RequestSyntax) **   <a name="Translate-UpdateParallelData-request-Name"></a>
The name of the parallel data resource being updated\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$`   
Required: Yes

 ** [ParallelDataConfig](#API_UpdateParallelData_RequestSyntax) **   <a name="Translate-UpdateParallelData-request-ParallelDataConfig"></a>
Specifies the format and S3 location of the parallel data input file\.  
Type: [ParallelDataConfig](API_ParallelDataConfig.md) object  
Required: Yes

## Response Syntax<a name="API_UpdateParallelData_ResponseSyntax"></a>

```
{
   "LatestUpdateAttemptAt": number,
   "LatestUpdateAttemptStatus": "string",
   "Name": "string",
   "Status": "string"
}
```

## Response Elements<a name="API_UpdateParallelData_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [LatestUpdateAttemptAt](#API_UpdateParallelData_ResponseSyntax) **   <a name="Translate-UpdateParallelData-response-LatestUpdateAttemptAt"></a>
The time that the most recent update was attempted\.  
Type: Timestamp

 ** [LatestUpdateAttemptStatus](#API_UpdateParallelData_ResponseSyntax) **   <a name="Translate-UpdateParallelData-response-LatestUpdateAttemptStatus"></a>
The status of the parallel data update attempt\. When the updated parallel data resource is ready for you to use, the status is `ACTIVE`\.  
Type: String  
Valid Values:` CREATING | UPDATING | ACTIVE | DELETING | FAILED` 

 ** [Name](#API_UpdateParallelData_ResponseSyntax) **   <a name="Translate-UpdateParallelData-response-Name"></a>
The name of the parallel data resource being updated\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$` 

 ** [Status](#API_UpdateParallelData_ResponseSyntax) **   <a name="Translate-UpdateParallelData-response-Status"></a>
The status of the parallel data resource that you are attempting to update\. Your update request is accepted only if this status is either `ACTIVE` or `FAILED`\.  
Type: String  
Valid Values:` CREATING | UPDATING | ACTIVE | DELETING | FAILED` 

## Errors<a name="API_UpdateParallelData_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** ConcurrentModificationException **   
Another modification is being made\. That modification must complete before you can make your change\.  
HTTP Status Code: 400

 ** ConflictException **   
There was a conflict processing the request\. Try your request again\.  
HTTP Status Code: 400

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidParameterValueException **   
The value of the parameter is not valid\. Review the value of the parameter you are using to correct it, and then retry your operation\.  
HTTP Status Code: 400

 ** InvalidRequestException **   
 The request that you made is not valid\. Check your request to determine why it's not valid and then retry the request\.   
HTTP Status Code: 400

 ** LimitExceededException **   
The specified limit has been exceeded\. Review your request and retry it with a quantity below the stated limit\.  
HTTP Status Code: 400

 ** ResourceNotFoundException **   
The resource you are looking for has not been found\. Review the resource you're looking for and see if a different resource will accomplish your needs before retrying the revised request\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\.  
HTTP Status Code: 400

## See Also<a name="API_UpdateParallelData_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/translate-2017-07-01/UpdateParallelData) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/translate-2017-07-01/UpdateParallelData) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/UpdateParallelData) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/UpdateParallelData) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/UpdateParallelData) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/translate-2017-07-01/UpdateParallelData) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/translate-2017-07-01/UpdateParallelData) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/translate-2017-07-01/UpdateParallelData) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/UpdateParallelData) 