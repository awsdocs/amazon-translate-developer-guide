# TranslationSettings<a name="API_TranslationSettings"></a>

Settings that configure the translation output\.

## Contents<a name="API_TranslationSettings_Contents"></a>

 ** Formality **   <a name="Translate-Type-TranslationSettings-Formality"></a>
You can optionally specify the desired level of formality for real\-time translations to supported target languages\. The formality setting controls the level of formal language usage \(also known as [register](https://en.wikipedia.org/wiki/Register_(sociolinguistics))\) in the translation output\. You can set the value to informal or formal\. If you don't specify a value for formality, or if the target language doesn't support formality, the translation will ignore the formality setting\.  
Note that asynchronous translation jobs don't support formality\. If you provide a value for formality, the `StartTextTranslationJob` API throws an exception \(InvalidRequestException\)\.  
For target languages that support formality, see [Supported Languages and Language Codes in the Amazon Translate Developer Guide](https://docs.aws.amazon.com/translate/latest/dg/what-is.html)\.  
Type: String  
Valid Values:` FORMAL | INFORMAL`   
Required: No

 ** Profanity **   <a name="Translate-Type-TranslationSettings-Profanity"></a>
Enable the profanity setting if you want Amazon Translate to mask profane words and phrases in your translation output\.  
To mask profane words and phrases, Amazon Translate replaces them with the grawlix string “?$\#@$“\. This 5\-character sequence is used for each profane word or phrase, regardless of the length or number of words\.  
Amazon Translate doesn't detect profanity in all of its supported languages\. For languages that support profanity detection, see [Supported Languages and Language Codes in the Amazon Translate Developer Guide](https://docs.aws.amazon.com/translate/latest/dg/what-is.html)\.  
Type: String  
Valid Values:` MASK`   
Required: No

## See Also<a name="API_TranslationSettings_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/TranslationSettings) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/TranslationSettings) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/TranslationSettings) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/TranslationSettings) 