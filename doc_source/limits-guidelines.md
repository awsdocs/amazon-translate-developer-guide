# Guidelines and Limits<a name="limits-guidelines"></a>

## Supported Regions<a name="translate-regions"></a>

For a list of AWS Regions where Amazon Translate is available, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#translate_region) in the *Amazon Web Services General Reference*\.

## Throttling<a name="limits-throttling"></a>

For information about throttling for Amazon Translate and to request a limit increase, see [Amazon Translate Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html#limits_amazon_translate) in the *Amazon Web Services General Reference*\.
+ Throttle rate per account: 100 transactions \(requests or operations\) per second \(tps\) with a burst limit of 120 tps\.

  Concurrent connections per account: 90 
+ Throttle rate per operation:    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/translate/latest/dg/limits-guidelines.html)

## Guidelines<a name="guidelines"></a>

Amazon Translate may store your content to continuously improve the quality of its analysis models\. See the [Amazon Translate FAQ](https://aws.amazon.com/translate/faqs/) to learn more\. 

You can request the deletion of existing data and that future data associated with your account not be stored by contacting AWS Support\. However, deleting your data may degrade your Amazon Translate results because it can remove unique training data that is helpful in improving results for your content\. 

## Service Limits<a name="limits"></a>

Amazon Translate has the following service limitations:


| Description | Limit | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Document size \(UTF\-8 characters\) | 5,000 bytes | 
| **Custom terminologies** |  | 
| Terminology file size | 10 Mb | 
| Maximum number of target languages per terminology file | 10 target languages | 
| Maximum number of existing terminologies per AWS account per region | 100 terminologies | 
| Maximum source text length per term | 200 bytes | 
| Maximum target text length per term | 200 bytes | 
| Maximum number of terms in the applied terminologies of a TranslateText response | 250\* | 

\* The 250 terms are the first 250 terms matched in the source text\. This limit is not per terminology, but rather for all terminologies used in a given TranslateText request\. Currently, the number of terminologies in a TranslateText request is limited to 1\. 