# Using do\-not\-translate tags in Amazon Translate<a name="customizing-translations-tags"></a>

You can add tags in your input content to specify text that you do not want to translate\. This feature is available for the console and for API operations\. 

**Topics**
+ [Using do\-not\-translate with the console](#console-tags)
+ [Using do\-not\-translate with the API](#api-tags)

## Using do\-not\-translate with the console<a name="console-tags"></a>

In the source text, use span tags to surround any text that you do not want to translate\. For example, to translate the following text from English to Italian:

```
Musée du Louvre, that's how you say Louvre Museum in French.
```

The text “Musée du Louvre” needs to remain in French, so we use a span tag around this content to skip translation:

```
<span translate="no">Musée du Louvre</span>, that's how you say Louvre Museum in French.
```

This sentence has the resulting Italian translation:

```
<span translate="no">Musée du Louvre</span>, così si dice Museo del Louvre in francese.
```

## Using do\-not\-translate with the API<a name="api-tags"></a>

You can use do\-not\-translate with the real\-time `TranslateText` and the asynchronous `TextTranslation` API operations\. In the source text that you provide for the API request, you can use any type of HTML element to specify content that needs to skip translation\. 

In the following example, we translate some text from English to Spanish, but leave some text in English:

```
aws translate translate-text \
  --source-language-code "en" \
  --target-language-code "es" \
  --region us-west-2 \
  --text "This can be translated to any language. <p translate=no>But do not translate this!</p>"
```

This API request returns the following Spanish translation:

```
{
    "TranslatedText": "Esto se puede traducir a cualquier idioma. 
                                <p translate=no>But do not translate this!</p>",
    "SourceLanguageCode": "en",
    "TargetLanguageCode": "es"
}
```