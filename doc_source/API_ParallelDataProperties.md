# ParallelDataProperties<a name="API_ParallelDataProperties"></a>

The properties of a parallel data resource\.

## Contents<a name="API_ParallelDataProperties_Contents"></a>

 ** Arn **   <a name="Translate-Type-ParallelDataProperties-Arn"></a>
The Amazon Resource Name \(ARN\) of the parallel data resource\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 512\.  
Required: No

 ** CreatedAt **   <a name="Translate-Type-ParallelDataProperties-CreatedAt"></a>
The time at which the parallel data resource was created\.  
Type: Timestamp  
Required: No

 ** Description **   <a name="Translate-Type-ParallelDataProperties-Description"></a>
The description assigned to the parallel data resource\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `[\P{M}\p{M}]{0,256}`   
Required: No

 ** EncryptionKey **   <a name="Translate-Type-ParallelDataProperties-EncryptionKey"></a>
The encryption key used to encrypt this object\.  
Type: [EncryptionKey](API_EncryptionKey.md) object  
Required: No

 ** FailedRecordCount **   <a name="Translate-Type-ParallelDataProperties-FailedRecordCount"></a>
The number of records unsuccessfully imported from the parallel data input file\.  
Type: Long  
Required: No

 ** ImportedDataSize **   <a name="Translate-Type-ParallelDataProperties-ImportedDataSize"></a>
The number of UTF\-8 characters that Amazon Translate imported from the parallel data input file\. This number includes only the characters in your translation examples\. It does not include characters that are used to format your file\. For example, if you provided a Translation Memory Exchange \(\.tmx\) file, this number does not include the tags\.  
Type: Long  
Required: No

 ** ImportedRecordCount **   <a name="Translate-Type-ParallelDataProperties-ImportedRecordCount"></a>
The number of records successfully imported from the parallel data input file\.  
Type: Long  
Required: No

 ** LastUpdatedAt **   <a name="Translate-Type-ParallelDataProperties-LastUpdatedAt"></a>
The time at which the parallel data resource was last updated\.  
Type: Timestamp  
Required: No

 ** LatestUpdateAttemptAt **   <a name="Translate-Type-ParallelDataProperties-LatestUpdateAttemptAt"></a>
The time that the most recent update was attempted\.  
Type: Timestamp  
Required: No

 ** LatestUpdateAttemptStatus **   <a name="Translate-Type-ParallelDataProperties-LatestUpdateAttemptStatus"></a>
The status of the most recent update attempt for the parallel data resource\.  
Type: String  
Valid Values:` CREATING | UPDATING | ACTIVE | DELETING | FAILED`   
Required: No

 ** Message **   <a name="Translate-Type-ParallelDataProperties-Message"></a>
Additional information from Amazon Translate about the parallel data resource\.   
Type: String  
Required: No

 ** Name **   <a name="Translate-Type-ParallelDataProperties-Name"></a>
The custom name assigned to the parallel data resource\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$`   
Required: No

 ** ParallelDataConfig **   <a name="Translate-Type-ParallelDataProperties-ParallelDataConfig"></a>
Specifies the format and S3 location of the parallel data input file\.  
Type: [ParallelDataConfig](API_ParallelDataConfig.md) object  
Required: No

 ** SkippedRecordCount **   <a name="Translate-Type-ParallelDataProperties-SkippedRecordCount"></a>
The number of items in the input file that Amazon Translate skipped when you created or updated the parallel data resource\. For example, Amazon Translate skips empty records, empty target texts, and empty lines\.  
Type: Long  
Required: No

 ** SourceLanguageCode **   <a name="Translate-Type-ParallelDataProperties-SourceLanguageCode"></a>
The source language of the translations in the parallel data file\.  
Type: String  
Length Constraints: Minimum length of 2\. Maximum length of 5\.  
Required: No

 ** Status **   <a name="Translate-Type-ParallelDataProperties-Status"></a>
The status of the parallel data resource\. When the parallel data is ready for you to use, the status is `ACTIVE`\.  
Type: String  
Valid Values:` CREATING | UPDATING | ACTIVE | DELETING | FAILED`   
Required: No

 ** TargetLanguageCodes **   <a name="Translate-Type-ParallelDataProperties-TargetLanguageCodes"></a>
The language codes for the target languages available in the parallel data file\. All possible target languages are returned as an array\.  
Type: Array of strings  
Length Constraints: Minimum length of 2\. Maximum length of 5\.  
Required: No

## See Also<a name="API_ParallelDataProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/ParallelDataProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/ParallelDataProperties) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/ParallelDataProperties) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/ParallelDataProperties) 