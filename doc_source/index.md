# Amazon Translate Developer Guide

-----
*****Copyright &copy; Amazon Web Services, Inc. and/or its affiliates. All rights reserved.*****

-----
Amazon's trademarks and trade dress may not be used in
connection with any product or service that is not Amazon's,
in any manner that is likely to cause confusion among customers,
or in any manner that disparages or discredits Amazon. All other
trademarks not owned by Amazon are the property of their respective
owners, who may or may not be affiliated with, connected to, or
sponsored by Amazon.

-----
## Contents
+ [What is Amazon Translate?](what-is.md)
+ [Supported languages and language codes](what-is-languages.md)
+ [How Amazon Translate works](how-it-works.md)
+ [Getting started with Amazon Translate](getting-started.md)
   + [Step 1: Set up an AWS account and create an administrator user](setting-up.md)
   + [Step 2: Set up the AWS Command Line Interface (AWS CLI)](setup-awscli.md)
   + [Step 3: Getting started (console)](get-started-console.md)
   + [Step 4: Getting started (AWS CLI)](get-started-cli.md)
   + [Step 5: Getting started (SDK)](get-started-sdk.md)
      + [Translating text using the AWS SDK for Java](examples-java.md)
      + [Translating text using the AWS SDK for Python (Boto)](examples-python.md)
      + [Translating text using the AWS Mobile SDK for Android](getting-started-android.md)
      + [Translating text using the AWS Mobile SDK for iOS](getting-started-ios.md)
+ [Translation processing modes](processing.md)
   + [Real-time translation](sync.md)
   + [Asynchronous batch processing with Amazon Translate](async.md)
      + [Prerequisites for batch translation jobs](async-prereqs.md)
      + [Running a batch translation job](async-start.md)
      + [Monitoring and analyzing batch translation jobs](async-monitor.md)
      + [Getting batch translation results](async-results.md)
+ [Customizing your translations with Amazon Translate](customizing-translations.md)
   + [Using do-not-translate tags in Amazon Translate](customizing-translations-tags.md)
   + [Customizing your translations with custom terminology](how-custom-terminology.md)
      + [Creating a custom terminology](creating-custom-terminology.md)
         + [Compatible languages](permissible-language-pairs.md)
      + [Using custom terminologies](using-ct.md)
      + [Encrypting your terminology](protect-terminology.md)
      + [Best practices](ct-best-practices.md)
   + [Masking profane words and phrases in Amazon Translate](customizing-translations-profanity.md)
   + [Setting formality in Amazon Translate](customizing-translations-formality.md)
   + [Customizing your translations with parallel data (Active Custom Translation)](customizing-translations-parallel-data.md)
      + [Parallel data input files for Amazon Translate](customizing-translations-parallel-data-input-files.md)
      + [Adding your parallel data to Amazon Translate](customizing-translations-parallel-data-adding.md)
      + [Viewing and managing your parallel data in Amazon Translate](customizing-translations-parallel-data-managing.md)
+ [Examples](examples.md)
   + [Using Amazon Polly with Amazon Translate](examples-polly.md)
   + [Using Amazon Translate to translate a chat channel](examples-twitch.md)
   + [Using Amazon Translate with Amazon DynamoDB](examples-ddb.md)
   + [Using Amazon Translate to translate a web page](examples-web.md)
   + [Using Amazon Translate to translate large documents](examples-split.md)
   + [Using Signature Version 4 with Amazon Translate](examples-sigv4.md)
+ [Security in Amazon Translate](security.md)
   + [Data protection in Amazon Translate](data-protection.md)
      + [Encryption at rest](encryption-at-rest.md)
      + [Encryption in transit](encryption-in-transit.md)
   + [Identity and access management for Amazon Translate](identity-and-access-management.md)
      + [How Amazon Translate works with IAM](security_iam_service-with-iam.md)
      + [Amazon Translate identity-based policy examples](security_iam_id-based-policy-examples.md)
      + [Troubleshooting Amazon Translate identity and access](security_iam_troubleshoot.md)
      + [Amazon Translate API permissions: Actions, resources, and conditions reference](translate-api-permissions-ref.md)
   + [Monitoring Amazon Translate](monitoring-translate.md)
      + [Logging Amazon Translate API calls with AWS CloudTrail](logging-using-cloudtrail.md)
      + [CloudWatch metrics and dimensions for Amazon Translate](translate-cloudwatch.md)
      + [Monitoring Amazon Translate events with Amazon EventBridge](monitoring-with-eventbridge.md)
   + [Compliance validation for Amazon Translate](compliance.md)
   + [Resilience in Amazon Translate](disaster-recovery-resiliency.md)
   + [Infrastructure security in Amazon Translate](infrastructure-security.md)
   + [Amazon Translate and interface VPC endpoints (AWS PrivateLink)](vpc-interface-endpoints.md)
+ [Guidelines and limits](what-is-limits.md)
+ [Document history for Amazon Translate](doc-history.md)
+ [API reference](api_reference.md)
+ [AWS glossary](glossary.md)