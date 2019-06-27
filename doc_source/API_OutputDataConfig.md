# OutputDataConfig<a name="API_OutputDataConfig"></a>

The output results configuration parameters for a batch translation job\.

## Contents<a name="API_OutputDataConfig_Contents"></a>

 **KmsKeyId**   <a name="Translate-Type-OutputDataConfig-KmsKeyId"></a>
The ID of the AWS Key Management Service \(KMS\) key that Amazon Translate uses to encrypt the output results of a translation job\. The `KmsKeyId` can be one of the following formats:  
+ KMS Key ID: "`1234abcd-12ab-34cd-56ef-1234567890ab`"
+ Amazon Resource Name \(ARN\) of a KMS Key: "`arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab`"
+ KMS Key Alias: "`alias/ExampleAlias`"
+ ARN of a KMS Key Alias: "`arn:aws:kms:us-west-2:111122223333:alias/ExampleAlias`"
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 400\.  
Pattern: `(arn:aws((-us-gov)|(-iso)|(-iso-b)|(-cn))?:kms:)?([a-z]{2}-[a-z]+(-[a-z]+)?-\d:)?(\d{12}:)?(((key/)?[a-zA-Z0-9-_]+)|(alias/[a-zA-Z0-9:/_-]+))`   
Required: No

 **S3Uri**   <a name="Translate-Type-OutputDataConfig-S3Uri"></a>
The URI of the S3 bucket in which to store the translation job's output\. The URI must be in the same Region as the API endpoint that you are calling\. The location is used as the prefix for the actual location of this output file\.  
When the translation job is finished, the service creates the output file in a directory specific to the job\. The `S3Uri` field contains the location of the output file, called `output.tar.gz`\. It is a compressed archive that contains the translated files\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: Yes

## See Also<a name="API_OutputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/OutputDataConfig) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/OutputDataConfig) 
+  [AWS SDK for Go \- Pilot](https://docs.aws.amazon.com/goto/SdkForGoPilot/translate-2017-07-01/OutputDataConfig) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/translate-2017-07-01/OutputDataConfig) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/translate-2017-07-01/OutputDataConfig) 