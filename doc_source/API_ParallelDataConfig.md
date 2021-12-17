# ParallelDataConfig<a name="API_ParallelDataConfig"></a>

Specifies the format and S3 location of the parallel data input file\.

## Contents<a name="API_ParallelDataConfig_Contents"></a>

 **Format**   <a name="Translate-Type-ParallelDataConfig-Format"></a>
The format of the parallel data input file\.  
Type: String  
Valid Values:` TSV | CSV | TMX`   
Required: Yes

 **S3Uri**   <a name="Translate-Type-ParallelDataConfig-S3Uri"></a>
The URI of the Amazon S3 folder that contains the parallel data input file\. The folder must be in the same Region as the API endpoint you are calling\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: Yes

## See Also<a name="API_ParallelDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/ParallelDataConfig) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/ParallelDataConfig) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/ParallelDataConfig) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/ParallelDataConfig) 