# Translating Text Using the AWS SDK for Python \(Boto\)<a name="examples-python"></a>

The following example demonstrates using the [TranslateText](API_TranslateText.md) operation in Python\. To run it, you must first install Amazon Translate via the AWS CLI\. For instructions, see [Step 2: Set Up the AWS Command Line Interface \(AWS CLI\)](setup-awscli.md)\.

```
import boto3

translate = boto3.client(service_name='translate', region_name='region', use_ssl=True)

result = translate.translate_text(Text="Hello, World", 
            SourceLanguageCode="en", TargetLanguageCode="de")
print('TranslatedText: ' + result.get('TranslatedText'))
print('SourceLanguageCode: ' + result.get('SourceLanguageCode'))
print('TargetLanguageCode: ' + result.get('TargetLanguageCode'))
```

You can change the source and target languages subject to the following constraints:
+ If the source language is English, you can translate the source text to any of the other supported languages\. For a list of supported languages, see [How It Works](how-it-works.md)\.
+ If the source language is not English, the target language must be English\.