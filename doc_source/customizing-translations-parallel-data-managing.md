# Viewing and managing your parallel data in Amazon Translate<a name="customizing-translations-parallel-data-managing"></a>

You can view all of the parallel data resources that you have added to Amazon Translate, and you can access detailed summaries for each one\. As your translation requirements change, you can refine your translation output by updating your parallel data\.

## Viewing and managing parallel data \(Amazon Translate console\)<a name="customizing-translations-parallel-data-managing-console"></a>

To view and manage your parallel data in the Amazon Translate console, use the **Parallel data** page:

**To view a list of your of parallel data resources**

1. Open the Amazon Translate console at [https://console\.aws\.amazon\.com/translate/](https://console.aws.amazon.com/translate/)

1. In the navigation menu on the left, choose **Customization**, and choose **Parallel data**\. The table on this page lists the parallel data resources that you have added to Amazon Translate\.

**To view the details for a parallel data resource**
+ On the **Parallel data** page, choose the name of the parallel data resource in the **Name** column\. The console opens the details page, which includes information such as the status, last updated date, source language, and target languages\.

**To update a parallel data resource**

1. Upload the updated version of your parallel data as a new input file in an Amazon S3 bucket\.

1. In the Amazon Translate console, go to the **Parallel data** page\.

1. Select the parallel data that you want to update, and choose **Update**\. The console shows the **Update parallel data** page\.

1. Provide the following:  
**Description \- optional**  
An updated description\.  
**Parallel data location on S3**  
The location of the updated parallel data input file in Amazon S3\. To provide the location by navigating to the file in Amazon S3, choose **Select file**\.  
**Select parallel data file format**  
The format of the parallel data input file\. Supported formats are Translation Memory eXchange \(TMX\), comma\-separated values \(CSV\), and tab\-separated values \(TSV\)\.

1. Choose **Save**\. Amazon Translate replaces the old parallel data with the new input file\.

## Viewing and managing parallel data \(AWS CLI\)<a name="customizing-translations-parallel-data-managing-cli"></a>

You can use the AWS CLI to view and update your parallel data resources\.

### To view a list of your parallel data resources<a name="customizing-translations-parallel-data-managing-cli-list"></a>

To view a list of the parallel data resources that you have added to Amazon Translate, use the `list-parallel-data` command\.

**Example list\-parallel\-data command**  
The following example returns a list of parallel data resources and their properties\.   

```
$ aws translate list-parallel-data
```
If the command succeeds, Amazon Translate returns an array like the following:  

```
{
    "ParallelDataPropertiesList": [
        {
            "Name": "my-parallel-data",
            "Arn": "arn:aws:translate:us-west-2:111122223333:parallel-data/my-parallel-data",
            "Status": "ACTIVE",
            "SourceLanguageCode": "en",
            "TargetLanguageCodes": [
                "es",
                "ja",
                "zh"
            ],
            "ParallelDataConfig": {
                "S3Uri": "s3://input-bucket/parallel-data-file.tsv",
                "Format": "TSV"
            },
            "ImportedDataSize": 2283,
            "ImportedRecordCount": 3,
            "FailedRecordCount": 0,
            "CreatedAt": 1598597751.406,
            "LastUpdatedAt": 1598597911.675
        }
    ]
}
```

### To view the details for a parallel data object<a name="customizing-translations-parallel-data-managing-cli-get"></a>

To look up the details for a single parallel data resource, use the `get-parallel-data` command\. This command returns the properties of the parallel data as well as a pre\-signed S3 URL where you can download the input file that was used to create it\.

**Example get\-parallel\-data command**  
The following example gets the properties and download location for the `my-parallel-data` object:  

```
$ aws translate get-parallel-data \
> --name my-parallel-data
```
If the command succeeds, Amazon Translate returns the properties and download location:  

```
{
    "ParallelDataProperties": {
        "Name": "my-parallel-data",
        "Arn": "arn:aws:translate:us-west-2:111122223333:parallel-data/my-parallel-data",
        "Status": "ACTIVE",
        "SourceLanguageCode": "en",
        "TargetLanguageCodes": [
            "es",
            "ja",
            "zh"
        ],
        "ParallelDataConfig": {
            "S3Uri": "s3://input-bucket/parallel-data-file.tsv",
            "Format": "TSV"
        },
        "ImportedDataSize": 2283,
        "ImportedRecordCount": 3,
        "FailedRecordCount": 0,
        "CreatedAt": 1598597751.406,
        "LastUpdatedAt": 1598597911.675
    },
    "DataLocation": {
        "RepositoryType": "S3",
        "Location": "pre-signed S3 URL"
    }
}
```

### To update a parallel data resource<a name="customizing-translations-parallel-data-managing-update"></a>

To update a parallel data resource, first, upload a new input file to an Amazon S3 input bucket\. Then, use the `update-parallel-data` command and specify the parallel data resource that you want to update\. Amazon Translate replaces the old parallel data with the information that's in the new input file\.

**Example update\-parallel\-data command**  
The following command updates `my-parallel-data` with a new input file from Amazon S3:  

```
$ aws translate update-parallel-data \
> --name my-parallel-data \
> --parallel-data-config S3Uri=s3://input-bucket/parallel-data-file.tsv,Format=TSV
```
If the command succeeds, Amazon Translate provides a response like the following:  

```
{
    "Name": "my-parallel-data",
    "Status": "ACTIVE",
    "LatestUpdateAttemptStatus": "UPDATING",
    "LatestUpdateAttemptAt": 1598601455.844
}
```
In this response, the `Status` field provides the status of the preexisting parallel data object, and the `LatestUpdateAttemptStatus` field provides the status of the current update attempt\.