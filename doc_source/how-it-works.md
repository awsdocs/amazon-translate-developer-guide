# How Amazon Translate Works<a name="how-it-works"></a>

Amazon Translate is based on neural networks that have been trained to translate between English and the following languages, or from these languages into English:
+ Arabic
+ Chinese \(Simplified\)
+ Chinese \(Traditional\)
+ Czech
+ French
+ German
+ Italian
+ Japanese
+ Portuguese
+ Russian
+ Spanish
+ Turkish

You can also translate text in any of these languages into another one of these languages by first translating the source text to English and then translating the English text to the target language\.

When working with Amazon Translate, you will provide source text and get output text:
+ **Source text**—The text that you want to translate\. You provide the source text in UTF\-8 format\.
+ **Output text**—The text that Amazon Translate has translated into the target language Output text is also in UTF\-8 format\. Depending on the source and target languages, there might be more characters in the output text than in the input text\.

The translation model has two components, the encoder and the decoder\. The *encoder* reads a source sentence one word at a time and constructs a semantic representation that captures its meaning\. The *decoder* uses the semantic representation to generate a translation one word at a time in the target language\.

Amazon Translate uses attention mechanisms to understand context\. This helps it decide which words in the source text are most relevant for generating the next target word\. Attention mechanisms enable the decoder to focus on the most relevant parts of a source sentence\. This ensures that the decoder correctly translates ambiguous words or phrases\. 

The target word that the model generates becomes input to the decoder\. The network continues generating words until it reaches the end of the sentence\.

To translate text, you call the [TranslateText](API_TranslateText.md) method and provide the source text and the target language, using the language code listed in the following table\.


| Language | Code | 
| --- | --- | 
| Arabic | ar | 
| Chinese \(Simplified\) | zh | 
| Chinese \(Traditional\) | zh\-TW | 
| Czech | cs | 
| English | en | 
| French | fr | 
| German | de | 
| Italian | it | 
| Japanese | ja | 
| Portuguese | pt | 
| Russian | ru | 
| Spanish | es | 
| Turkish | tr | 

To translate text from any non\-English language in the table to any other non\-English language in the table, translate it into English, and then translate the English output text into the target language\.

Amazon Translate can automatically detect the source language\. For automatic language detection, specify `auto` as the source language\. when you provide source text\. Amazon Translate calls Amazon Comprehend to detect the source language\. 

## Automatic Language Detection<a name="how-to-auto"></a>

Amazon Translate can automatically detect the language used in your source text\. To use automatic language detection, specify `auto` as the source language\. Amazon Translate calls Amazon Comprehend on your behalf to determine the language used in the source text\. By choosing automatic language detection, you agree to the service terms and agreements for Amazon Comprehend\. For information about pricing for Amazon Comprehend, see [ Amazon Comprehend Pricing ](https://aws.amazon.com/comprehend/pricing/)\.

## Exception Handling<a name="how-to-error-msg"></a>

If you specify a source or target language that isn't supported, Amazon Translate returns the following exceptions: 
+ **UnsupportedLanguagePairException** – Amazon Translate supports translation between English and the six other languages\. Either the source language or the target language must be English\. 
+ **DetectedLanguageLowConfidenceException** – If you use automatic language detection, and Amazon Translate has low confidence that it detected the correct source language, it returns this exception\. If a low confidence level is acceptable, you can use the source language returned in the exception\.

## Next Steps<a name="how-it-works-next-steps"></a>

Now that you've learned about Amazon Translate you can explore the following sections to learn about creating a solution\.
+ [Getting Started with Amazon Translate](getting-started.md)
+ [Examples](examples.md)