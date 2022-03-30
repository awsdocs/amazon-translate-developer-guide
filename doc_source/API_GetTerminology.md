# GetTerminology<a name="API_GetTerminology"></a>

Retrieves a custom terminology\.

## Request Syntax<a name="API_GetTerminology_RequestSyntax"></a>

```
{
   "Name": "string",
   "TerminologyDataFormat": "string"
}
```

## Request Parameters<a name="API_GetTerminology_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Name](#API_GetTerminology_RequestSyntax) **   <a name="Translate-GetTerminology-request-Name"></a>
The name of the custom terminology being retrieved\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$`   
Required: Yes

 ** [TerminologyDataFormat](#API_GetTerminology_RequestSyntax) **   <a name="Translate-GetTerminology-request-TerminologyDataFormat"></a>
The data format of the custom terminology being retrieved\.  
If you don't specify this parameter, Amazon Translate returns a file with the same format as the file that was imported to create the terminology\.   
If you specify this parameter when you retrieve a multi\-directional terminology resource, you must specify the same format as the input file that was imported to create it\. Otherwise, Amazon Translate throws an error\.  
Type: String  
Valid Values:` CSV | TMX | TSV`   
Required: No

## Response Syntax<a name="API_GetTerminology_ResponseSyntax"></a>

```
{
   "AuxiliaryDataLocation": { 
      "Location": "string",
      "RepositoryType": "string"
   },
   "TerminologyDataLocation": { 
      "Location": "string",
      "RepositoryType": "string"
   },
   "TerminologyProperties": { 
      "Arn": "string",
      "CreatedAt": number,
      "Description": "string",
      "Directionality": "string",
      "EncryptionKey": { 
         "Id": "string",
         "Type": "string"
      },
      "Format": "string",
      "LastUpdatedAt": number,
      "Message": "string",
      "Name": "string",
      "SizeBytes": number,
      "SkippedTermCount": number,
      "SourceLanguageCode": "string",
      "TargetLanguageCodes": [ "string" ],
      "TermCount": number
   }
}
```

## Response Elements<a name="API_GetTerminology_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [AuxiliaryDataLocation](#API_GetTerminology_ResponseSyntax) **   <a name="Translate-GetTerminology-response-AuxiliaryDataLocation"></a>
The Amazon S3 location of a file that provides any errors or warnings that were produced by your input file\. This file was created when Amazon Translate attempted to create a terminology resource\. The location is returned as a presigned URL to that has a 30\-minute expiration\.  
Type: [TerminologyDataLocation](API_TerminologyDataLocation.md) object

 ** [TerminologyDataLocation](#API_GetTerminology_ResponseSyntax) **   <a name="Translate-GetTerminology-response-TerminologyDataLocation"></a>
The Amazon S3 location of the most recent custom terminology input file that was successfully imported into Amazon Translate\. The location is returned as a presigned URL that has a 30\-minute expiration\.  
Amazon Translate doesn't scan all input files for the risk of CSV injection attacks\.   
CSV injection occurs when a \.csv or \.tsv file is altered so that a record contains malicious code\. The record begins with a special character, such as =, \+, \-, or @\. When the file is opened in a spreadsheet program, the program might interpret the record as a formula and run the code within it\.  
Before you download an input file from Amazon S3, ensure that you recognize the file and trust its creator\.
Type: [TerminologyDataLocation](API_TerminologyDataLocation.md) object

 ** [TerminologyProperties](#API_GetTerminology_ResponseSyntax) **   <a name="Translate-GetTerminology-response-TerminologyProperties"></a>
The properties of the custom terminology being retrieved\.  
Type: [TerminologyProperties](API_TerminologyProperties.md) object

## Errors<a name="API_GetTerminology_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidParameterValueException **   
The value of the parameter is not valid\. Review the value of the parameter you are using to correct it, and then retry your operation\.  
HTTP Status Code: 400

 ** ResourceNotFoundException **   
The resource you are looking for has not been found\. Review the resource you're looking for and see if a different resource will accomplish your needs before retrying the revised request\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\.  
HTTP Status Code: 400

## See Also<a name="API_GetTerminology_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/translate-2017-07-01/GetTerminology) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/translate-2017-07-01/GetTerminology) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/GetTerminology) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/GetTerminology) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/GetTerminology) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/translate-2017-07-01/GetTerminology) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/translate-2017-07-01/GetTerminology) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/translate-2017-07-01/GetTerminology) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/GetTerminology) 