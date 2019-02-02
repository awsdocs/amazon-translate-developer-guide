# TerminologyProperties<a name="API_TerminologyProperties"></a>

## Contents<a name="API_TerminologyProperties_Contents"></a>

 **Arn**   <a name="Translate-Type-TerminologyProperties-Arn"></a>
Type: String  
Pattern: `^arn:aws((-us-gov)|(-cn))?:translate:[a-zA-Z0-9-]+:[0-9]{12}:terminology/.+?/.+?$`   
Required: No

 **CreatedAt**   <a name="Translate-Type-TerminologyProperties-CreatedAt"></a>
Type: Timestamp  
Required: No

 **Description**   <a name="Translate-Type-TerminologyProperties-Description"></a>
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `[\P{M}\p{M}]{0,256}`   
Required: No

 **EncryptionKey**   <a name="Translate-Type-TerminologyProperties-EncryptionKey"></a>
Type: [EncryptionKey](API_EncryptionKey.md) object  
Required: No

 **LastUpdatedAt**   <a name="Translate-Type-TerminologyProperties-LastUpdatedAt"></a>
Type: Timestamp  
Required: No

 **Name**   <a name="Translate-Type-TerminologyProperties-Name"></a>
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([A-Za-z0-9-]_?)+$`   
Required: No

 **SizeBytes**   <a name="Translate-Type-TerminologyProperties-SizeBytes"></a>
Type: Integer  
Required: No

 **SourceLanguageCode**   <a name="Translate-Type-TerminologyProperties-SourceLanguageCode"></a>
Type: String  
Length Constraints: Minimum length of 2\. Maximum length of 5\.  
Required: No

 **TargetLanguageCodes**   <a name="Translate-Type-TerminologyProperties-TargetLanguageCodes"></a>
Type: Array of strings  
Length Constraints: Minimum length of 2\. Maximum length of 5\.  
Required: No

 **TermCount**   <a name="Translate-Type-TerminologyProperties-TermCount"></a>
Type: Integer  
Required: No

## See Also<a name="API_TerminologyProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/TerminologyProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/TerminologyProperties) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/translate-2017-07-01/TerminologyProperties) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/translate-2017-07-01/TerminologyProperties) 