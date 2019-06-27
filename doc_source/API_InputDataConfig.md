# InputDataConfig<a name="API_InputDataConfig"></a>

The input properties for requesting a batch translation job\.

## Contents<a name="API_InputDataConfig_Contents"></a>

 **S3Uri**   <a name="Translate-Type-InputDataConfig-S3Uri"></a>
The AWS S3 URI for the input data\. The S3 bucket must be in the same Region as the API endpoint you are calling\.  
The URI can point to a single input file, or it can provide the prefix for a collection of input files\. For example\. if you use the URI `S3://bucketName/prefix` and the prefix is a single file, Amazon Translate uses that files as input\. If more than one file begins with the prefix, Amazon Translate uses all of them as input\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: Yes

## See Also<a name="API_InputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/InputDataConfig) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/InputDataConfig) 
+  [AWS SDK for Go \- Pilot](https://docs.aws.amazon.com/goto/SdkForGoPilot/translate-2017-07-01/InputDataConfig) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/translate-2017-07-01/InputDataConfig) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/translate-2017-07-01/InputDataConfig) 