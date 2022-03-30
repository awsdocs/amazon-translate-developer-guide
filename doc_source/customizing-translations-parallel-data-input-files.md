# Parallel data input files for Amazon Translate<a name="customizing-translations-parallel-data-input-files"></a>

Before you can create a parallel data resource in Amazon Translate, you must create an input file that contains your translation examples\. Your parallel data input file must use languages that Amazon Translate supports\. For a list of these languages, see [Supported languages and language codes](what-is.md#what-is-languages)\.

## Example parallel data<a name="customizing-translations-parallel-data-input-files-example-pd"></a>

The text in the following table provides examples of translation segments that can be formatted into a parallel data input file:


| en | es | zh | 
| --- | --- | --- | 
|  Amazon Translate is a neural machine translation service\.  |  Amazon Translate es un servicio de traducción automática basado en redes neuronales\.  |  Amazon Translate 是一项神经机器翻译服务。  | 
|  Neural machine translation is a form of language translation automation that uses deep learning models\.  |  La traducción automática neuronal es una forma de automatizar la traducción de lenguajes utilizando modelos de aprendizaje profundo\.  |  神经机器翻译使用深度学习模型，是一种语言翻译自动化的形式。  | 
|  Amazon Translate allows you to localize content for international users\.  |  Amazon Translate le permite localizar contenido para usuarios internacionales\.  |  Amazon Translate 允许您为国际用户本地化内容。  | 

The first row of the table provides the language codes\. The first language, English \(en\), is the source language\. Spanish \(es\) and Chinese \(zh\) are the target languages\. The first column provides examples of source text\. The other columns contain examples of translations\. When this parallel data customizes a batch job, Amazon Translate adapts the translation to reflect the examples\. 

## Input file formats<a name="customizing-translations-parallel-data-input-files-formats"></a>

Amazon Translate supports the following formats for parallel data input files:
+ Translation Memory eXchange \(TMX\)
+ Comma\-separated values \(CSV\)
+ Tab\-separated values \(TSV\)

------
#### [ TMX ]



**Example TMX input file**  
The following example TMX file defines parallel data in a format that Amazon Translate accepts\. In this file, English \(`en`\) is the source language\. Spanish \(`es`\) and Chinese \(`zh`\) are the target languages\. As an input file for parallel data, it provides several examples that Amazon Translate can use to tailor the output of a batch job\.  

```
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
    <header srclang="en"/>
    <body>
        <tu>
            <tuv xml:lang="en">
                <seg>Amazon Translate is a neural machine translation service.</seg>
            </tuv>
            <tuv xml:lang="es">
                <seg>Amazon Translate es un servicio de traducción automática basado en redes neuronales.</seg>
            </tuv>
            <tuv xml:lang="zh">
                <seg>Amazon Translate 是一项神经机器翻译服务。</seg>
            </tuv>
        </tu>
        <tu>
            <tuv xml:lang="en">
                <seg>Neural machine translation is a form of language translation automation that uses deep learning models.</seg>
            </tuv>
            <tuv xml:lang="es">
                <seg>La traducción automática neuronal es una forma de automatizar la traducción de lenguajes utilizando modelos de aprendizaje profundo.</seg>
            </tuv>
            <tuv xml:lang="zh">
                <seg>神经机器翻译使用深度学习模型，是一种语言翻译自动化的形式。</seg>
            </tuv>
        </tu>
        <tu>
            <tuv xml:lang="en">
                <seg>Amazon Translate allows you to localize content for international users.</seg>
            </tuv>
            <tuv xml:lang="es">
                <seg>Amazon Translate le permite localizar contenido para usuarios internacionales.</seg>
            </tuv>
            <tuv xml:lang="zh">
                <seg>Amazon Translate 允许您为国际用户本地化内容。</seg>
            </tuv>
        </tu>
    </body>
</tmx>
```

**TMX requirements**

Remember the following requirements from Amazon Translate when you define your parallel data in a TMX file:
+ Amazon Translate supports TMX 1\.4b\. For more information, see the [TMX 1\.4b specification](https://www.gala-global.org/tmx-14b#SectionReferences) on the Globalization and Localization Association website\.
+ The `header` element must include the `srclang` attribute\. The value of this attribute determines the source language of the parallel data\.
+ The `body` element must contain at least one translation unit \(`tu`\) element\.
+ Each `tu` element must contain at least two translation unit variant \(`tuv`\) elements\. One of these `tuv` elements must have an `xml:lang` attribute that has the same value as the one assigned to the `srclang` attribute in the `header` element\.
+ All `tuv` elements must have the `xml:lang` attribute\.
+ All `tuv` elements must have a segment \(`seg`\) element\.
+ While processing your input file, Amazon Translate skips certain `tu` or `tuv` elements if it encounters `seg` elements that are empty or contain only white space:
  + If the `seg` element corresponds to the source language, Amazon Translate skips the `tu` element that the `seg` element occupies\.
  + If the `seg` element corresponds to a target language, Amazon Translate skips only the `tuv` element that the `seg` element occupies\.
+ While processing your input file, Amazon Translate skips certain `tu` or `tuv` elements if it encounters `seg` elements that exceed 1000 bytes:
  + If the `seg` element corresponds to the source language, Amazon Translate skips the `tu` element that the `seg` element occupies\.
  + If the `seg` element corresponds to a target language, Amazon Translate skips only the `tuv` element that the `seg` element occupies\.
+ If the input file contains multiple `tu` elements with the same source text, Amazon Translate does one of the following:
  + If the `tu` elements have the `changedate` attribute, it uses the element with the most recent date\.
  + Otherwise, it uses the element that occurs closest to the end of the file\.

------
#### [ CSV ]

The following example CSV file defines parallel data in a format that Amazon Translate accepts\. In this file, English \(`en`\) is the source language\. Spanish \(`es`\) and Chinese \(`zh`\) are the target languages\. As an input file for parallel data, it provides several examples that Amazon Translate can use to tailor the output of a batch job\.

**Example CSV input file**  

```
en,es,zh
Amazon Translate is a neural machine translation service.,Amazon Translate es un servicio de traducción automática basado en redes neuronales.,Amazon Translate 是一项神经机器翻译服务。
Neural machine translation is a form of language translation automation that uses deep learning models.,La traducción automática neuronal es una forma de automatizar la traducción de lenguajes utilizando modelos de aprendizaje profundo.,神经机器翻译使用深度学习模型，是一种语言翻译自动化的形式。
Amazon Translate allows you to localize content for international users.,Amazon Translate le permite localizar contenido para usuarios internacionales.,Amazon Translate 允许您为国际用户本地化内容。
```

**CSV requirements**

Remember the following requirements from Amazon Translate when you define your parallel data in a CSV file:
+ The first row consists of the language codes\. The first code is the source language, and each subsequent code is a target language\.
+ Each field in the first column contains source text\. Each field in a subsequent column contains a target translation\.
+ If the text in any field contains a comma, the text must be enclosed in double quote \("\) characters\.
+ A text field cannot span multiple lines\.
+ Fields cannot start with the following characters: \+, \-, =, @\. This requirement applies whether or not the field is enclosed in double quotes \("\)\.
+ If the text in a field contains a double quote \("\), it must be escaped with a double quote\. For example, text such as:

  ```
  34" monitor
  ```

  Must be written as:

  ```
  34"" monitor
  ```
+ While processing your input file, Amazon Translate will skip certain lines or fields if it encounters fields that are empty or contain only white space:
  + If a source text field is empty, Amazon Translate skips the line that it occupies\.
  + If a target translation field is empty, Amazon Translate skips only that field\.
+ While processing your input file, Amazon Translate skips certain lines or fields if it encounters fields that exceed 1000 bytes:
  + If a source text field exceeds the byte limit, Amazon Translate skips the line that it occupies\.
  + If a target translation field exceeds the byte limit, Amazon Translate skips only that field\.
+ If the input file contains multiple records with the same source text, Amazon Translate uses the record that occurs closest to the end of the file\.

------
#### [ TSV ]

The following example TSV file defines parallel data in a format that Amazon Translate accepts\. In this file, English \(`en`\) is the source language\. Spanish \(`es`\) and Chinese \(`zh`\) are the target languages\. As an input file for parallel data, it provides several examples that Amazon Translate can use to tailor the output of a batch job\.

**Example TSV input file**  

```
en	es	zh
Amazon Translate is a neural machine translation service.	Amazon Translate es un servicio de traducción automática basado en redes neuronales.	Amazon Translate 是一项神经机器翻译服务。
Neural machine translation is a form of language translation automation that uses deep learning models.	La traducción automática neuronal es una forma de automatizar la traducción de lenguajes utilizando modelos de aprendizaje profundo.	神经机器翻译使用深度学习模型，是一种语言翻译自动化的形式。
Amazon Translate allows you to localize content for international users.	Amazon Translate le permite localizar contenido para usuarios internacionales.	Amazon Translate 允许您为国际用户本地化内容。
```

**TSV requirements**

Remember the following requirements from Amazon Translate when you define your parallel data in a TSV file:
+ The first row consists of the language codes\. The first code is the source language, and each subsequent code is a target language\.
+ Each field in the first column contains source text\. Each field in a subsequent column contains a target translation\.
+ If the text in any field contains a tab character, the text must be enclosed in double quote \("\) characters\.
+ A text field cannot span multiple lines\.
+ Fields cannot start with the following characters: \+, \-, =, @\. This requirement applies whether or not the field is enclosed in double quotes \("\)\.
+ If the text in a field contains a double quote \("\), it must be escaped with a double quote\. For example, text such as:

  ```
  34" monitor
  ```

  Must be written as:

  ```
  34"" monitor
  ```
+ While processing your input file, Amazon Translate skips certain lines or fields if it encounters fields that are empty or contain only white space:
  + If a source text field is empty, Amazon Translate skips the line that it occupies\.
  + If a target translation field is empty, Amazon Translate skips only that field\.
+ While processing your input file, Amazon Translate skips certain lines or fields if it encounters fields that exceed 1000 bytes:
  + If a source text field exceeds the byte limit, Amazon Translate skips the line that it occupies\.
  + If a target translation field exceeds the byte limit, Amazon Translate skips only that field\.
+ If the input file contains multiple records with the same source text, Amazon Translate uses the record that occurs closest to the end of the file\.

------