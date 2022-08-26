# Setting formality in Amazon Translate<a name="customizing-translations-formality"></a>

You can optionally specify the desired level of *formality* for translations to supported target languages\. The formality setting controls the level of formal language usage \(also known as [honorifics](https://en.wikipedia.org/wiki/Honorifics_(linguistics)) or [register](https://en.wikipedia.org/wiki/Register_(sociolinguistics)#Register_as_formality_scale)\) in the translation output\. The formality setting is available for real\-time translation and asynchronous batch processing\.

Formality supports the following values:
+ **Informal** – All sentences in the translated text use language constructs associated with informal communication\. For example, translated text uses the familiar form of second person pronouns and their verb agreement \(or Kudaketa form for Japanese\)\.
+ **Formal** – All sentences in the translated text use language constructs associated with formal, polite communication\. For example, translated text uses the formal form of second person pronouns and their verb agreement \(or Teineigo form for Japanese\)\. 

For example, the sentence ‘Are you sure?’ can have two correct translations in German: ‘Sind Sie sicher?’ for the formal register and ‘Bist du sicher?’ for the informal one\.

If Amazon Translate doesn’t support formality level for the target language, or you don't specify the formality parameter, the translation job ignores the formality setting\.

## Using the formality setting<a name="customizing-translations-formality-using"></a>

To set formality in a real\-time translation request, do one of the following:
+ On the **Real\-time translation** page in the Amazon Translate console, under **Additional settings**, enable the **Formality** setting and select one of the values\.
+ Use the Settings parameter in the [TranslateText](https://docs.aws.amazon.com/translate/latest/APIReference/API_TranslateText.html) operation in the Amazon Translate API\.
+ For the `translate-text` command in the AWS CLI, set the `--settings` parameter to `Formality=FORMAL` or `Formality=INFORMAL`\. For more information, see [translate\-text](https://docs.aws.amazon.com/cli/latest/reference/translate/translate-text.html) in the *AWS CLI Command Reference*\. 

To set formality in a batch translation request, set the **Formality** parameter when you start the translation job\. For details and examples, see [Running a batch translation job](async-start.md)\.

For CLI or API requests, the `AppliedSettings` field in the response includes the formality setting \(if any\) from the request\. If the target language doesn't support formality, the `AppliedSettings` value in the response is NULL\.

## Supported languages<a name="customizing-translations-formality-languages"></a>

Amazon Translate supports the formality setting for translation from any source language to the following target languages\. Formality does not support variants of these languages \(such as fr\-CA and es\-MX\) as the target language\.


| Language | Language code | 
| --- | --- | 
| French | fr | 
| German | de | 
| Hindi | hi | 
| Italian | it | 
| Japanese | ja | 
| Spanish | es | 

For all the languages that Amazon Translate supports, see [Supported languages and language codes](what-is-languages.md)\.