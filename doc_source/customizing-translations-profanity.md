# Masking profane words and phrases in Amazon Translate<a name="customizing-translations-profanity"></a>

When you run translations with Amazon Translate, you can enable the *profanity* setting to mask profane words and phrases in your translation output\. 

To mask profane words and phrases, Amazon Translate replaces them with the grawlix string “?$\#@$“\. This 5\-character sequence is used for each profane word or phrase, regardless of the length or number of words\.

Amazon Translate does not mask profanity in translation requests where the source language and target language are the same\.

In some cases, a profane word in the source input might naturally become inoffensive in the translated output\. In such cases, no masking is applied\.

Amazon Translate detects each profane word or phrase literally, not contextually\. This means that it might mask a profane word even if it’s inoffensive in context\. For example, if Amazon Translate detected “jerk” as a profane word, then it would write the phrase “jerk chicken” as “?$\#@$ chicken”, even though “jerk chicken” is inoffensive\. \(Here, “jerk” is used as an example only\. Amazon Translate does not detect that word as profanity\.\)

**Topics**
+ [Using the profanity setting](#customizing-translations-profanity-using)
+ [Unsupported languages](#customizing-translations-profanity-languages)

## Using the profanity setting<a name="customizing-translations-profanity-using"></a>

You can use the profanity setting with both types of translation operations in Amazon Translate: real\-time translation and asynchronous batch processing\.

To mask profanity in a real\-time translation request, do any of the following:
+ On the **Real\-time translation** page in the Amazon Translate console, under **Additional settings**, enable the **Profanity** setting\.
+ For `translate-text` command in the AWS CLI, set the `--settings` parameter to `Profanity=MASK`\. For more information, see [TranslateText](https://docs.aws.amazon.com/translate/latest/APIReference/API_TranslateText.html) in the *AWS CLI Command Reference*\.
+ Use the Settings parameter in the [TranslateText](http://amazonaws.com/translate/latest/dg/API_TranslateText.html) action in the Amazon Translate API\.

To mask profanity in an asynchronous batch operation, see [Running a batch translation job](async-start.md)\.

## Unsupported languages<a name="customizing-translations-profanity-languages"></a>

You can mask profanity when you translate to any of the target languages that Amazon Translate supports, with the following exceptions:


| Language | Language code | 
| --- | --- | 
| Bengali | bn | 
| Hindi | hi | 
| Malayalam | ml | 
| Punjabi | pa | 
| Sinhala | si | 
| Vietnamese | vi | 

For all of the languages that Amazon Translate supports, see [Supported languages and language codes](what-is-languages.md)\.