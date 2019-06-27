# StartTextTranslationJob<a name="API_StartTextTranslationJob"></a>

Starts an asynchronous batch translation job\. Batch translation jobs can be used to translate large volumes of text across multiple files at once\. It is not necessary to use English \(`en`\) as either the source or the target language, but not all language combinations are supported by Amazon Translate\. For more information, see [Supported Language Pairs](https://docs.aws.amazon.com/translate/latest/dg/what-is-language-pairs.html)\.
+ Arabic \(ar\)
+ Chinese \(Simplified\) \(zh\)
+ Chinese \(Traditional\) \(zh\-TW\)
+ Czech \(cs\)
+ Danish \(da\)
+ Dutch \(nl\)
+ English \(en\)
+ Finnish \(fi\)
+ French \(fr\)
+ German \(de\)
+ Hebrew \(he\)
+ Hindi \(hi\)
+ Indonesian \(id\)
+ Italian \(it\)
+ Japanese \(ja\)
+ Korean \(ko\)
+ Malay \(ms\)
+ Norwegian \(no\)
+ Persian \(fa\)
+ Polish \(pl\)
+ Portuguese \(pt\)
+ Russian \(ru\)
+ Spanish \(es\)
+ Swedish \(sv\)
+ Turkish \(tr\)

Batch translation jobs can be described with the [DescribeTextTranslationJob](API_DescribeTextTranslationJob.md) operation, listed with the [ListTextTranslationJobs](API_ListTextTranslationJobs.md) operation, and stopped with the [StopTextTranslationJob](API_StopTextTranslationJob.md) operation\.

**Note**  
Amazon Translate does not support batch translation of multiple source languages at once\.

## Request Syntax<a name="API_StartTextTranslationJob_RequestSyntax"></a>

```
{
   "[ClientToken](#Translate-StartTextTranslationJob-request-ClientToken)": "string",
   "[DataAccessRoleArn](#Translate-StartTextTranslationJob-request-DataAccessRoleArn)": "string",
   "[InputDataConfig](#Translate-StartTextTranslationJob-request-InputDataConfig)": { 
      "[S3Uri](API_InputDataConfig.md#Translate-Type-InputDataConfig-S3Uri)": "string"
   },
   "[JobName](#Translate-StartTextTranslationJob-request-JobName)": "string",
   "[OutputDataConfig](#Translate-StartTextTranslationJob-request-OutputDataConfig)": { 
      "[KmsKeyId](API_OutputDataConfig.md#Translate-Type-OutputDataConfig-KmsKeyId)": "string",
      "[S3Uri](API_OutputDataConfig.md#Translate-Type-OutputDataConfig-S3Uri)": "string"
   },
   "[SourceLanguageCode](#Translate-StartTextTranslationJob-request-SourceLanguageCode)": "string",
   "[TargetLanguageCode](#Translate-StartTextTranslationJob-request-TargetLanguageCode)": "string",
   "[TerminologyNames](#Translate-StartTextTranslationJob-request-TerminologyNames)": [ "string" ],
   "[VpcConfig](#Translate-StartTextTranslationJob-request-VpcConfig)": { 
      "[SecurityGroupIds](API_VpcConfig.md#Translate-Type-VpcConfig-SecurityGroupIds)": [ "string" ],
      "[Subnets](API_VpcConfig.md#Translate-Type-VpcConfig-Subnets)": [ "string" ]
   }
}
```

## Request Parameters<a name="API_StartTextTranslationJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientToken](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-ClientToken"></a>
The client token of the EC2 instance calling the request\. Use the [DescribeInstances](docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeInstances.html) EC2 operation to retreive an instance's client token\. For more information, see [Client Tokens](docs.aws.amazon.com/AWSEC2/latest/APIReference/Run_Instance_Idempotency.html#client-tokens) in the EC2 User Guide\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: Yes

 ** [DataAccessRoleArn](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of an AWS Identity Access and Management \(IAM\) role that grants Amazon Translate read access to your input data\. For more nformation, see [Authentication and Access Control for Amazon Translate](auth-and-access-control.md)\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [InputDataConfig](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-InputDataConfig"></a>
Specifies the format and location of the input data for the job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: Yes

 ** [JobName](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-JobName"></a>
The name of the batch translation job to be performed\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** [OutputDataConfig](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-OutputDataConfig"></a>
Specifies the location to which which your job output will be saved\. If this bucket is encrypted, be sure to include the relevant KMS encryption key\.  
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: Yes

 ** [SourceLanguageCode](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-SourceLanguageCode"></a>
The language code for the language of the source text files\. The language must be a language supported by Amazon Translate\.  
Type: String  
Length Constraints: Minimum length of 2\. Maximum length of 5\.  
Required: Yes

 ** [TargetLanguageCode](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-TargetLanguageCode"></a>
The language code requested for the language of the target text\. The language must be a language supported by Amazon Translate\.  
Type: String  
Length Constraints: Minimum length of 2\. Maximum length of 5\.  
Required: Yes

 ** [TerminologyNames](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-TerminologyNames"></a>
The name of a terminology to use in the batch translation job\. For a list of available terminologies, use the [ListTerminologies](API_ListTerminologies.md) operation\.  
Type: Array of strings  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$`   
Required: No

 ** [VpcConfig](#API_StartTextTranslationJob_RequestSyntax) **   <a name="Translate-StartTextTranslationJob-request-VpcConfig"></a>
The VPC security groups and subnets that are attached to the EC2 instance calling the request\.  
Type: [VpcConfig](API_VpcConfig.md) object  
Required: No

## Response Syntax<a name="API_StartTextTranslationJob_ResponseSyntax"></a>

```
{
   "[JobId](#Translate-StartTextTranslationJob-response-JobId)": "string",
   "[JobStatus](#Translate-StartTextTranslationJob-response-JobStatus)": "string"
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
+  `FAILED` \- The job did not complete\. To get details, use the [DescribeTextTranslationJob](API_DescribeTextTranslationJob.md) operation\.
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | COMPLETED_WITH_ERROR | FAILED | STOP_REQUESTED | STOPPED` 

## Errors<a name="API_StartTextTranslationJob_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidParameterValueException**   
The value of the parameter is invalid\. Review the value of the parameter you are using to correct it, and then retry your operation\.  
HTTP Status Code: 400

 **InvalidRequestException**   
 The request that you made is invalid\. Check your request to determine why it's invalid and then retry the request\.   
HTTP Status Code: 400

 **TooManyRequestsException**   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\.  
HTTP Status Code: 400

 **UnsupportedLanguagePairException**   
Amazon Translate does not support translation from the language of the source text into the requested target language\. For more information, see [Exception Handling](how-it-works.md#how-to-error-msg)\.   
HTTP Status Code: 400

## See Also<a name="API_StartTextTranslationJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for Go \- Pilot](https://docs.aws.amazon.com/goto/SdkForGoPilot/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/translate-2017-07-01/StartTextTranslationJob) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/translate-2017-07-01/StartTextTranslationJob) 