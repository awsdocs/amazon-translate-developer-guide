# InputDataConfig<a name="API_InputDataConfig"></a>

The input configuration properties for requesting a batch translation job\.

## Contents<a name="API_InputDataConfig_Contents"></a>

 **ContentType**   <a name="Translate-Type-InputDataConfig-ContentType"></a>
Describes the format of the data that you submit to Amazon Translate as input\. You can specify one of the following multipurpose internet mail extension \(MIME\) types:  
+  `text/html`: The input data consists of one or more HTML files\. Amazon Translate translates only the text that resides in the `html` element in each file\.
+  `text/plain`: The input data consists of one or more unformatted text files\. Amazon Translate translates every character in this type of input\.
+  `application/vnd.openxmlformats-officedocument.wordprocessingml.document`: The input data consists of one or more Word documents \(\.docx\)\.
+  `application/vnd.openxmlformats-officedocument.presentationml.presentation`: The input data consists of one or more PowerPoint Presentation files \(\.pptx\)\.
+  `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet`: The input data consists of one or more Excel Workbook files \(\.xlsx\)\.
+  `application/x-xliff+xml`: The input data consists of one or more XML Localization Interchange File Format \(XLIFF\) files \(\.xlf\)\. Amazon Translate supports only XLIFF version 1\.2\.
If you structure your input data as HTML, ensure that you set this parameter to `text/html`\. By doing so, you cut costs by limiting the translation to the contents of the `html` element in each file\. Otherwise, if you set this parameter to `text/plain`, your costs will cover the translation of every character\.
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `^[-\w.]+\/[-\w.+]+$`   
Required: Yes

 **S3Uri**   <a name="Translate-Type-InputDataConfig-S3Uri"></a>
The URI of the AWS S3 folder that contains the input file\. The folder must be in the same Region as the API endpoint you are calling\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: Yes

## See Also<a name="API_InputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/InputDataConfig) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/InputDataConfig) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/translate-2017-07-01/InputDataConfig) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/translate-2017-07-01/InputDataConfig) 