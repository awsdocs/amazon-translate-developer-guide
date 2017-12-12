# How It Works<a name="how-it-works"></a>


|  | 
| --- |
| This is prerelease documentation for a service in preview release\. It is subject to change\. | 

Amazon Translate is based on neural networks\. Once trained on a language pair, Amazon Translate can translate between the two languages\.

The model has two components, the encoder and the decoder\. The encoder reads the source sentence one word at a time and constructs a semantic representation that captures the meaning of the source text\. The decoder uses the semantic representation to generate a translation one word at a time in the target language\.

Amazon Translate uses attention mechanisms to understand context and decide which words in the source are most relevant for generating the next target word\. The attention mechanisms enable the decoder to shift focus on certain parts of the source sentence to make sure that ambiguous words or phrases are translated correctly\. The next word that the neural network generates becomes an input to the decoder and the network continues generating words until it reaches the end of the sentence\.

Amazon Translate machine translates text from one of six languages into English and from English into one of the six languages\. You just call the [TranslateText](API_TranslateText.md) method with the text you want to translate, and specify the source and target languages\. Amazon Translate returns the translated text\.

+ **Source text** – The text that you want to translate in UTF\-8 format\.

+ **Output text** – Amazon Translate translates the source text into the target language and returns the translated text in UTF\-8 format\. The number of characters in the output text may be larger than the input text depending on the source and target languages\.

You can translate text from English \(en\) into the following languages, or from the following languages to English:


| Language | Code | 
| --- | --- | 
| Arabic | ar | 
| Chinese \(Simplified\) | zh | 
| French | fr | 
| German | de | 
| Portuguese | pt | 
| Spanish | es | 

To translate from any non\-English language on the list to any other non\-English language on the list, first translate the source language into English, and then translate the English text to the target language\. 

## Error Handling<a name="how-to-error-msg"></a>

If you specify a source or target language that isn't supported, Amazon Translate sends one of the following exceptions: 

+ **UnsupportedLanguagePairException** – Amazon Translate supports translation between English and other languages\. Either the source or target language must be English; otherwise, you get this error\.