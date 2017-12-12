# TranslateText<a name="API_TranslateText"></a>

Translates input text from the source language to the target language\. You can translate between English \(en\) and one of the following languages, or between one of the following languages and English\.

+ Arabic \(ar\)

+ Chinese \(Simplified\) \(zh\)

+ French \(fr\)

+ German \(de\)

+ Portuguese \(pt\)

+ Spanish \(es\)

## Request Syntax<a name="API_TranslateText_RequestSyntax"></a>

```
{
   "SourceLanguageCode": "string",
   "TargetLanguageCode": "string",
   "Text": "string"
}
```

## Request Parameters<a name="API_TranslateText_RequestParameters"></a>

For information about the parameters that are common to all actions, see Common Parameters\.

The request accepts the following data in JSON format\.

 ** SourceLanguageCode **   
One of the supported language codes for the source text\. If the `TargetLanguageCode` is not "en", the `SourceLanguageCode` must be "en"\.  
Type: String  
Length Constraints: Minimum length of 2\. Maximum length of 5\.  
Required: Yes

 ** TargetLanguageCode **   
One of the supported language codes for the target text\. If the `SourceLanguageCode` is not "en", the `TargetLanguageCode` must be "en"\.  
Type: String  
Length Constraints: Minimum length of 2\. Maximum length of 5\.  
Required: Yes

 ** Text **   
The text to translate\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 1000\.  
Required: Yes

## Response Syntax<a name="API_TranslateText_ResponseSyntax"></a>

```
{
   "SourceLanguageCode": "string",
   "TargetLanguageCode": "string",
   "TranslatedText": "string"
}
```

## Response Elements<a name="API_TranslateText_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** SourceLanguageCode **   
The language code for the language of the input text\.   
Type: String  
Length Constraints: Minimum length of 2\. Maximum length of 5\.

 ** TargetLanguageCode **   
The language code for the language of the translated text\.   
Type: String  
Length Constraints: Minimum length of 2\. Maximum length of 5\.

 ** TranslatedText **   
The text translated into the target language\.  
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_TranslateText_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **ServiceUnavailableException**   
Amazon Translate is unavailable\. Retry your request later\.  
HTTP Status Code: 400

 **TextSizeLimitExceededException**   
The size of the input text exceeds the length constraint for the `Text` field\. Try again with a shorter text\.   
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

 **UnsupportedLanguagePairException**   
Amazon Translate cannot translate input text in the source language into this target language\. For more information, see [Error Handling](how-it-works.md#how-to-error-msg)\.   
HTTP Status Code: 400

## See Also<a name="API_TranslateText_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS Command Line Interface](http://docs.aws.amazon.com/goto/aws-cli/translate-2017-07-01/TranslateText) 

+  [AWS SDK for \.NET](http://docs.aws.amazon.com/goto/DotNetSDKV3/translate-2017-07-01/TranslateText) 

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/TranslateText) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/TranslateText) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/translate-2017-07-01/TranslateText) 

+  [AWS SDK for JavaScript](http://docs.aws.amazon.com/goto/AWSJavaScriptSDK/translate-2017-07-01/TranslateText) 

+  [AWS SDK for PHP V3](http://docs.aws.amazon.com/goto/SdkForPHPV3/translate-2017-07-01/TranslateText) 

+  [AWS SDK for Python](http://docs.aws.amazon.com/goto/boto3/translate-2017-07-01/TranslateText) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/translate-2017-07-01/TranslateText) 