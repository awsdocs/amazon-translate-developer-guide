# ParallelDataDataLocation<a name="API_ParallelDataDataLocation"></a>

The location of the most recent parallel data input file that was successfully imported into Amazon Translate\.

## Contents<a name="API_ParallelDataDataLocation_Contents"></a>

 **Location**   <a name="Translate-Type-ParallelDataDataLocation-Location"></a>
The Amazon S3 location of the parallel data input file\. The location is returned as a presigned URL to that has a 30 minute expiration\.  
Amazon Translate doesn't scan parallel data input files for the risk of CSV injection attacks\.   
CSV injection occurs when a \.csv or \.tsv file is altered so that a record contains malicious code\. The record begins with a special character, such as =, \+, \-, or @\. When the file is opened in a spreadsheet program, the program might interpret the record as a formula and run the code within it\.  
Before you download a parallel data input file from Amazon S3, ensure that you recognize the file and trust its creator\.
Type: String  
Length Constraints: Maximum length of 10000\.  
Pattern: `[\P{M}\p{M}]{0,10000}`   
Required: Yes

 **RepositoryType**   <a name="Translate-Type-ParallelDataDataLocation-RepositoryType"></a>
Describes the repository that contains the parallel data input file\.  
Type: String  
Length Constraints: Maximum length of 10000\.  
Pattern: `[\P{M}\p{M}]{0,10000}`   
Required: Yes

## See Also<a name="API_ParallelDataDataLocation_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/ParallelDataDataLocation) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/ParallelDataDataLocation) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/ParallelDataDataLocation) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/ParallelDataDataLocation) 