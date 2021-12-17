# Customizing Your Translations with Parallel Data \(Active Custom Translation\)<a name="customizing-translations-parallel-data"></a>

Add *parallel data* to Amazon Translate to customize the output of your batch translations jobs\. Parallel data consists of examples that show how you want segments of text to be translated\. It includes a collection of textual examples in a source language, and for each example, it contains the desired translation output in one or more target languages\.

When you add parallel data to a batch translation job, you create an *Active Custom Translation* job\. When you run these jobs, Amazon Translate uses your parallel data at runtime to produce customized machine translation output\. It adapts the translation to reflect the style, tone, and word choices that it finds in your parallel data\. With parallel data, you can tailor your translations for terms or phrases that are unique to a specific domain, such as life sciences, law or finance\.

**Note**  
Active Custom Translation jobs are priced at a higher rate than other jobs that don't use parallel data\. For more information, see [Amazon Translate pricing](http://aws.amazon.com/translate/pricing/)\.

For example, the following parallel data is defined in a CSV file:

```
"en","fr"
"How are you?","Comment ça va ?"
```

In this example, English \(`en`\) is the source language, and French \(`fr`\) is the target language\. The example shows how the source phrase "How are you?" should be translated into French\. After this example input file is imported into Amazon Translate, it can be applied to translation jobs to influence their output\. During such jobs, Amazon Translate translates "How are you?" into the informal “Comment ça va ?” as opposed to the formal “Comment allez\-vous ?” For example, the job might receive the following source text:

```
Hello, how are you?
How are you?
Hi, how are you?
How are you doing?
```

From this text, the job produces the following translation:

```
Bonjour, comment ça va ?
Comment ça va ?
Salut, comment ça va ?
Comment ça va ?
```

In contrast, if the job runs without the parallel data, the output might include the more formal "comment allez\-vous":

```
Bonjour, comment allez-vous ?
Comment allez-vous ?
Salut, comment allez-vous ?
Comment allez-vous ?
```

By customizing your batch translation jobs with parallel data, you influence the output in a way that's similar to using a custom translation model that you train with your translation examples\. With Active Custom Translation, training a custom model is unnecessary, and you avoid the time and expense that such training requires\. As your translation requirements change over time, you can refine your output by updating your parallel data, which is easier than retraining a custom model\. 

## Region Availability<a name="customizing-translations-parallel-data-regions"></a>

Active Custom Translation is available in the following regions:
+ US East \(N\. Virginia\)
+ US West \(Oregon\)
+ Europe \(Ireland\)

**Topics**
+ [Region Availability](#customizing-translations-parallel-data-regions)
+ [Parallel Data Input Files for Amazon Translate](customizing-translations-parallel-data-input-files.md)
+ [Adding Your Parallel Data to Amazon Translate](customizing-translations-parallel-data-adding.md)
+ [Viewing and Managing Your Parallel Data in Amazon Translate](customizing-translations-parallel-data-managing.md)