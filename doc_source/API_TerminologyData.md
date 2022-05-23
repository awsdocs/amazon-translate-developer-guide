# TerminologyData<a name="API_TerminologyData"></a>

The data associated with the custom terminology\. For information about the custom terminology file, see [ Creating a Custom Terminology](https://docs.aws.amazon.com/translate/latest/dg/creating-custom-terminology.html)\.

## Contents<a name="API_TerminologyData_Contents"></a>

 ** Directionality **   <a name="Translate-Type-TerminologyData-Directionality"></a>
The directionality of your terminology resource indicates whether it has one source language \(uni\-directional\) or multiple \(multi\-directional\)\.    
UNI  
The terminology resource has one source language \(for example, the first column in a CSV file\), and all of its other languages are target languages\.   
MULTI  
Any language in the terminology resource can be the source language or a target language\. A single multi\-directional terminology resource can be used for jobs that translate different language pairs\. For example, if the terminology contains English and Spanish terms, it can be used for jobs that translate English to Spanish and Spanish to English\.
When you create a custom terminology resource without specifying the directionality, it behaves as uni\-directional terminology, although this parameter will have a null value\.  
Type: String  
Valid Values:` UNI | MULTI`   
Required: No

 ** File **   <a name="Translate-Type-TerminologyData-File"></a>
The file containing the custom terminology data\. Your version of the AWS SDK performs a Base64\-encoding on this field before sending a request to the AWS service\. Users of the SDK should not perform Base64\-encoding themselves\.  
Type: Base64\-encoded binary data object  
Length Constraints: Maximum length of 10485760\.  
Required: Yes

 ** Format **   <a name="Translate-Type-TerminologyData-Format"></a>
The data format of the custom terminology\.  
Type: String  
Valid Values:` CSV | TMX | TSV`   
Required: Yes

## See Also<a name="API_TerminologyData_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/TerminologyData) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/TerminologyData) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/TerminologyData) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/TerminologyData) 