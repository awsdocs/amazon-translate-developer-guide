# DeleteParallelData<a name="API_DeleteParallelData"></a>

Deletes a parallel data resource in Amazon Translate\.

## Request Syntax<a name="API_DeleteParallelData_RequestSyntax"></a>

```
{
   "Name": "string"
}
```

## Request Parameters<a name="API_DeleteParallelData_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Name](#API_DeleteParallelData_RequestSyntax) **   <a name="Translate-DeleteParallelData-request-Name"></a>
The name of the parallel data resource that is being deleted\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$`   
Required: Yes

## Response Syntax<a name="API_DeleteParallelData_ResponseSyntax"></a>

```
{
   "Name": "string",
   "Status": "string"
}
```

## Response Elements<a name="API_DeleteParallelData_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [Name](#API_DeleteParallelData_ResponseSyntax) **   <a name="Translate-DeleteParallelData-response-Name"></a>
The name of the parallel data resource that is being deleted\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$` 

 ** [Status](#API_DeleteParallelData_ResponseSyntax) **   <a name="Translate-DeleteParallelData-response-Status"></a>
The status of the parallel data deletion\.  
Type: String  
Valid Values:` CREATING | UPDATING | ACTIVE | DELETING | FAILED` 

## Errors<a name="API_DeleteParallelData_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **ConcurrentModificationException**   
Another modification is being made\. That modification must complete before you can make your change\.  
HTTP Status Code: 400

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **ResourceNotFoundException**   
The resource you are looking for has not been found\. Review the resource you're looking for and see if a different resource will accomplish your needs before retrying the revised request\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\.  
HTTP Status Code: 400

## See Also<a name="API_DeleteParallelData_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/translate-2017-07-01/DeleteParallelData) 
+  [ AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/translate-2017-07-01/DeleteParallelData) 
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/DeleteParallelData) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/DeleteParallelData) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/DeleteParallelData) 
+  [ AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/translate-2017-07-01/DeleteParallelData) 
+  [ AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/translate-2017-07-01/DeleteParallelData) 
+  [ AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/translate-2017-07-01/DeleteParallelData) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/DeleteParallelData) 