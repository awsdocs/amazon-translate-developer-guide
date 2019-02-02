# Amazon Translate Developer Guide

-----
*****Copyright &copy; 2019 Amazon Web Services, Inc. and/or its affiliates. All rights reserved.*****

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
+ [What Is Amazon Translate?](what-is.md)
   + [Supported Language Pairs](pairs.md)
+ [How Amazon Translate Works](how-it-works.md)
+ [Getting Started with Amazon Translate](getting-started.md)
   + [Step 1: Set Up an AWS Account and Create an Administrator User](setting-up.md)
   + [Step 2: Set Up the AWS Command Line Interface (AWS CLI)](setup-awscli.md)
   + [Step 3: Getting Started (Console)](get-started-console.md)
   + [Step 4: Getting Started (AWS CLI)](get-started-cli.md)
   + [Step 5: Getting Started (SDK)](get-started-sdk.md)
      + [Translating Text Using the AWS SDK for Java](examples-java.md)
      + [Translating Text Using the AWS SDK for Python (Boto)](examples-python.md)
      + [Translating Text Using the AWS Mobile SDK for Android](getting-started-android.md)
      + [Translating Text Using the AWS Mobile SDK for iOS](getting-started-ios.md)
+ [Custom Terminology](how-custom-terminology.md)
   + [Creating a Custom Terminology](creating-custom-terminology.md)
      + [Compatible Languages](permissible-language-pairs.md)
   + [Using Custom Terminologies](using-ct.md)
   + [Encrypting Your Terminology](protect-terminology.md)
   + [Best Practices](ct-best-practices.md)
+ [Examples](examples.md)
   + [Using Amazon Polly with Amazon Translate](examples-polly.md)
   + [Using Amazon Translate to Translate a Chat Channel](examples-twitch.md)
   + [Using Amazon Translate with Amazon DynamoDB](examples-ddb.md)
   + [Using Amazon Translate to Translate a Web Page](examples-web.md)
   + [Using Amazon Translate to Translate Large Documents](examples-split.md)
   + [Using Signature Version 4 with Amazon Translate](examples-sigv4.md)
+ [Authentication and Access Control for Amazon Translate](auth-and-access-control.md)
   + [Overview of Managing Access Permissions to Your Amazon Translate Resources](access-control-overview.md)
   + [Using Identity-Based Policies (IAM Policies) for Amazon Translate](access-control-managing-permissions.md)
   + [Amazon Translate API Permissions: Actions, Resources, and Conditions Reference](translate-api-permissions-ref.md)
+ [Monitoring Amazon Translate](monitoring-translate.md)
   + [CloudWatch Metrics and Dimensions for Amazon Translate](translate-cloudwatch.md)
+ [Guidelines and Limits](limits-guidelines.md)
+ [Document History for Amazon Translate](doc-history.md)
+ [API Reference](API_Reference.md)
   + [Actions](API_Operations.md)
      + [DeleteTerminology](API_DeleteTerminology.md)
      + [GetTerminology](API_GetTerminology.md)
      + [ImportTerminology](API_ImportTerminology.md)
      + [ListTerminologies](API_ListTerminologies.md)
      + [TranslateText](API_TranslateText.md)
   + [Data Types](API_Types.md)
      + [AppliedTerminology](API_AppliedTerminology.md)
      + [EncryptionKey](API_EncryptionKey.md)
      + [Term](API_Term.md)
      + [TerminologyData](API_TerminologyData.md)
      + [TerminologyDataLocation](API_TerminologyDataLocation.md)
      + [TerminologyProperties](API_TerminologyProperties.md)
   + [Common Errors](CommonErrors.md)
   + [Common Parameters](CommonParameters.md)
+ [AWS Glossary](glossary.md)