# ImportTerminology<a name="API_ImportTerminology"></a>

Creates or updates a custom terminology, depending on whether one already exists for the given terminology name\. Importing a terminology with the same name as an existing one will merge the terminologies based on the chosen merge strategy\. The only supported merge strategy is OVERWRITE, where the imported terminology overwrites the existing terminology of the same name\.

If you import a terminology that overwrites an existing one, the new terminology takes up to 10 minutes to fully propagate\. After that, translations have access to the new terminology\.

## Request Syntax<a name="API_ImportTerminology_RequestSyntax"></a>

```
{
   "Description": "string",
   "EncryptionKey": { 
      "Id": "string",
      "Type": "string"
   },
   "MergeStrategy": "string",
   "Name": "string",
   "TerminologyData": { 
      "Directionality": "string",
      "File": blob,
      "Format": "string"
   }
}
```

## Request Parameters<a name="API_ImportTerminology_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Description](#API_ImportTerminology_RequestSyntax) **   <a name="Translate-ImportTerminology-request-Description"></a>
The description of the custom terminology being imported\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `[\P{M}\p{M}]{0,256}`   
Required: No

 ** [EncryptionKey](#API_ImportTerminology_RequestSyntax) **   <a name="Translate-ImportTerminology-request-EncryptionKey"></a>
The encryption key for the custom terminology being imported\.  
Type: [EncryptionKey](API_EncryptionKey.md) object  
Required: No

 ** [MergeStrategy](#API_ImportTerminology_RequestSyntax) **   <a name="Translate-ImportTerminology-request-MergeStrategy"></a>
The merge strategy of the custom terminology being imported\. Currently, only the OVERWRITE merge strategy is supported\. In this case, the imported terminology will overwrite an existing terminology of the same name\.  
Type: String  
Valid Values:` OVERWRITE`   
Required: Yes

 ** [Name](#API_ImportTerminology_RequestSyntax) **   <a name="Translate-ImportTerminology-request-Name"></a>
The name of the custom terminology being imported\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$`   
Required: Yes

 ** [TerminologyData](#API_ImportTerminology_RequestSyntax) **   <a name="Translate-ImportTerminology-request-TerminologyData"></a>
The terminology data for the custom terminology being imported\.  
Type: [TerminologyData](API_TerminologyData.md) object  
Required: Yes

## Response Syntax<a name="API_ImportTerminology_ResponseSyntax"></a>

```
{
   "AuxiliaryDataLocation": { 
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

## Response Elements<a name="API_ImportTerminology_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [AuxiliaryDataLocation](#API_ImportTerminology_ResponseSyntax) **   <a name="Translate-ImportTerminology-response-AuxiliaryDataLocation"></a>
The Amazon S3 location of a file that provides any errors or warnings that were produced by your input file\. This file was created when Amazon Translate attempted to create a terminology resource\. The location is returned as a presigned URL to that has a 30 minute expiration\.  
Type: [TerminologyDataLocation](API_TerminologyDataLocation.md) object

 ** [TerminologyProperties](#API_ImportTerminology_ResponseSyntax) **   <a name="Translate-ImportTerminology-response-TerminologyProperties"></a>
The properties of the custom terminology being imported\.  
Type: [TerminologyProperties](API_TerminologyProperties.md) object

## Errors<a name="API_ImportTerminology_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidParameterValueException **   
The value of the parameter is not valid\. Review the value of the parameter you are using to correct it, and then retry your operation\.  
HTTP Status Code: 400

 ** LimitExceededException **   
The specified limit has been exceeded\. Review your request and retry it with a quantity below the stated limit\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\.  
HTTP Status Code: 400

## See Also<a name="API_ImportTerminology_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/translate-2017-07-01/ImportTerminology) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/translate-2017-07-01/ImportTerminology) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/ImportTerminology) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/ImportTerminology) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/ImportTerminology) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/translate-2017-07-01/ImportTerminology) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/translate-2017-07-01/ImportTerminology) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/translate-2017-07-01/ImportTerminology) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/ImportTerminology) 