# Guidelines and limits<a name="what-is-limits"></a>

The following sections contain information about Amazon Translate guidelines and limits\.

**Topics**
+ [Supported AWS Regions](#what-is-regions)
+ [Compliance](#what-is-compliance)
+ [Throttling](#limits-throttling)
+ [Guidelines](#guidelines)
+ [Service limits](#limits)

## Supported AWS Regions<a name="what-is-regions"></a>

For a list of AWS Regions that support Amazon Translate, see the [AWS Region Table](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) or [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#translate_region) in the *Amazon Web Services General Reference*\.

## Compliance<a name="what-is-compliance"></a>

For more information about Amazon Translate compliance programs, see [AWS Compliance](https://aws.amazon.com/compliance/), [AWS Compliance Programs](https://aws.amazon.com/compliance/programs/), and [AWS Services in Scope by Compliance Program](https://aws.amazon.com/compliance/services-in-scope)\.

## Throttling<a name="limits-throttling"></a>

Amazon Translate scales to serve customer operational traffic\. If you encounter sustained throttling, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.

## Guidelines<a name="guidelines"></a>

To continuously improve the quality of its analysis models, Amazon Translate might store your data\. To learn more, see the [Amazon Translate FAQ](https://aws.amazon.com/translate/faqs/)\. 

You can request that we delete your data and that future data associated with your account isn't stored by contacting [AWS Support](https://console.aws.amazon.com/support/home#/)\. However, because deleting your data can also delete unique training data that is helpful in improving translation, doing so might reduce the quality of your translations\. 

## Service limits<a name="limits"></a>

Amazon Translate has the following service limitations\.


**Synchronous real\-time translation limits**  

| Description | Limit | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Maximum document size \(UTF\-8 characters\) | 5,000 bytes | 


**Asynchronous batch translation limits**  

| Description | Limit | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Maximum number of characters per document | 1,000,000 | 
| Maximum size per document | 20 MB | 
| Maximum size of translatable text in a single document | 1 MB | 
| Maximum number of target languages in a batch job request | 10 | 
| Maximum number of documents in batch | 1,000,000 | 
| Maximum size of total documents in batch | 5 GB | 
| Maximum number of concurrent batch translation jobs | 10 | 
| Maximum number of queued batch translation jobs | 1000 | 
| Transactions per second for the StartTextTranslationJob API action | 5 | 
| Transactions per second for the DescribeTextTranslationJob API action | 10 | 
| Transactions per second for the ListTextTranslationJobs API action | 10 | 
| Transactions per second for the StopTextTranslationJob API action | 5 | 


**Custom terminology limits**  

| Description | Limit | 
| --- | --- | 
| Maximum custom terminology file size | 10 MB | 
| Maximum number of custom terminology files per AWS account per AWS Region | 100 | 
| Maximum number of target languages per custom terminology file | 10 | 
| Maximum source and target text length per custom terminology term | 200 bytes | 
| Maximum number of terminology files per TranslateText or StartTextTranslationJob request\. | 1 | 
| Transactions per second for the ImportTerminology API action | 5 | 
| Transactions per second for the GetTerminology API action | 10 | 
| Transactions per second for the ListTerminologies API action | 10 | 
| Transactions per second for the DeleteTerminology API action | 5 | 


**Parallel data limits**  

| Description | Limit | 
| --- | --- | 
| Maximum number of parallel data resources per AWS account per AWS Region | 1000 | 
| Maximum parallel data input file size | 5 GB | 
| Maximum number of source languages in a parallel data resource | 1 | 
| Maximum size of a single segment or record in a parallel data input file | 1000 bytes | 
| Maximum number of concurrent create or update operations for parallel data resources | 1 | 
| Transactions per second for the CreateParallelData API action | 5 | 
| Transactions per second for the GetParallelData API action | 10 | 
| Transactions per second for the ListParallelData API action | 10 | 
| Transactions per second for the UpdateParallelData API action | 5 | 
| Transactions per second for the DeleteParallelData API action | 5 | 