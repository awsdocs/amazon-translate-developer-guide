# Creating a custom terminology<a name="creating-custom-terminology"></a>

You can use a CSV, TSV, or TMX file with the source text and the target \(translated\) term for the terminology file\. A single source text is used for each term, but there can be multiple target terms, one for each language, as long as the target and source language can be used\.

**Important**  
The source word within a custom terminology is *case\-sensitive* and will not work for words that are not an exact match\.

## Directionality<a name="creating-custom-terminology-directionality"></a>

When you create custom terminology in Amazon Translate, you can choose the following types for *directionality*, which indicates whether your terminology has one or multiple source languages\.

**Uni\-directional**  
The file contains one source language\. All other languages are target languages\. For example, if your terminology file is a CSV file, then the first column contains text in the source language, and all other columns contain text in the target languages\.

**Multi\-directional**  
Any language in the file can be a source language or a target language\. For example, if your terminology file contains text in English, Chinese, and Spanish, then you could use the same file for jobs that translate the following language pairs:  
+ English to Chinese
+ English to Spanish
+ Chinese to English
+ Chinese to Spanish
+ Spanish to English
+ Spanish to Chinese

In contrast, if you used uni\-directional terminology for those translation jobs, then you would need to create three terminology files\. Each file would have the same content, but each would use English, Chinese, or Spanish as the source language respectively\. 

## Example terminology files<a name="creating-custom-terminology-examples"></a>

See [Supported languages and language codes](what-is-languages.md) for the supported language codes\.

**CSV \(comma separated values\)**


|  |  |  |  | 
| --- |--- |--- |--- |
|  en  |  fr  |  de  |  es  | 
|  Amazon  |  Amazon  |  Amazon  |  Amazon  | 

**TMX \(Translation Memory eXchange\) **

A TMX file is an XML\-type file commonly used by translation software\. Although the form is different than the CSV, the content is similar:

```
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
 <header
    creationtool="XYZTool" creationtoolversion="0"
    datatype="PlainText" segtype="sentence"
    adminlang="en-us" srclang="en"
    o-tmf="test"/>
 <body>
   <tu>
     <tuv xml:lang="en">
       <seg>Amazon</seg>
     </tuv>
     <tuv xml:lang="fr">
       <seg>Amazon</seg>
     </tuv>
     <tuv xml:lang="de">
       <seg>Amazon</seg>
     </tuv>
     <tuv xml:lang="es">
       <seg>Amazon</seg>
     </tuv>
   </tu>   
 </body>
</tmx>
```

These files are then attached to your Amazon Translate account\. When a translation job is run and you choose to use the custom terminology, Amazon Translate then uses the designated word whenever it encounters the source word\.