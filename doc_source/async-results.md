# Getting batch translation results<a name="async-results"></a>

Once the job's status is `COMPLETED` or `COMPLETED_WITH_ERROR`, your output documents are available in the Amazon S3 folder you specified\. The output document names match the input document names, with the addition of the target language code as a prefix\. For instance, if you translated a document called `mySourceText.txt` into French, the output document will be called `fr.mySourceText.txt`\.

If the status of a batch translation job is `FAILED`, the [DescribeTextTranslationJob](API_DescribeTextTranslationJob.md) operation response includes a `Message` field that describes the reason why the job didn't complete successfully\.

Each batch translation job also generates an auxiliary file that contains information on the translations performed, such as the total number of characters translated and the number of errors encountered\. This file, called `target-language-code.auxiliary-translation-details.json`, is generated in the `details` subfolder of your output folder\.

The following is an example of a batch translation auxiliary file\.

```
{
  "sourceLanguageCode": "en",
  "targetLanguageCode": "fr",
  "charactersTranslated": "105",
  "documentCountWithCustomerError": "0",
  "documentCountWithServerError": "0",
  "inputDataPrefix": "s3://input-bucket-name/folder",
  "outputDataPrefix": "s3://output-bucket-name/012345678901-TranslateText-1c1838f470806ab9c3e0057f14717bed/",
  "details": [
    {
      "sourceFile": "mySourceText.txt",
      "targetFile": "fr.mySourceText.txt",
      "auxiliaryData": {
        "appliedTerminologies": [
          {
            "name": "TestTerminology",
            "terms": [
              {
                "sourceText": "Amazon",
                "targetText": "Amazon"
              }
            ]
          }
        ]
      }
    },
    {
      "sourceFile": "batchText.txt",
      "targetFile": "fr.batchText.txt",
      "auxiliaryData": {
        "appliedTerminologies": [
          {
            "name": "TestTerminology",
            "terms": [
              {
                "sourceText": "Amazon",
                "targetText": "Amazon"
              }
            ]
          }
        ]
      }
    }
  ]
}
```