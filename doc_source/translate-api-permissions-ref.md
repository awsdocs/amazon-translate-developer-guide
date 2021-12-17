# Amazon Translate API Permissions: Actions, Resources, and Conditions Reference<a name="translate-api-permissions-ref"></a>

Use the following table as a reference when writing a permissions policy that you can attach to an IAM identity \(an identity\-based policy\)\. The list includes each Amazon Translate API operation, the corresponding action for which you can grant permissions, and the AWS resource for which you can grant the permissions\. You specify the actions in the policy's `Action` field, and you specify the resource value in the policy's `Resource` field\. 

To express conditions, you can use AWS\-wide condition keys in your Amazon Translate policies\. For a complete list of AWS\-wide keys, see [Available Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\. 

**Note**  
To specify an action, use the `translate:` prefix followed by the API operation name, for example, `translate:TranslateText`\.

Use the scroll bars to see the rest of the table\.


**Amazon Translate API and Required Permissions for Actions**  

| Amazon Translate API Operations | Required Permissions \(API Actions\) | Resources | 
| --- | --- | --- | 
| [TranslateText](API_TranslateText.md) – Use to specify the source language \. |  `translate:TranslateText`  | \* | 
| [TranslateText](API_TranslateText.md) – Use for automatic source language detection\. |  `translate:TranslateText` `comprehend:DetectDominantLanguage`  | \* | 
| [DeleteTerminology](API_DeleteTerminology.md) – Use for deleting a custom terminology from your account\. |  `translate:DeleteTerminology`  | \* | 
| [GetTerminology](API_GetTerminology.md) – Use for retrieving information about a custom terminology associated with your account\. |  `translate:GetTerminology` If the terminology uses KMS encryption, it also requires that the following permissions be set in the KMS key policy \(not an IAM policy\): `kms:Decrypt`  | \* | 
| [ImportTerminology](API_ImportTerminology.md) – Use for importing a custom terminology to your account\. |  `translate:ImportTerminology` If the terminology uses AWS KMS encryption, it also requires that the following permissions be set in the AWS KMS key policy \(not an IAM policy\): `kms:CreateGrant` `kms:DescribeKey` `kms:GenerateDataKey` `kms:RetireGrant`  | \* | 
| [ListTerminologies](API_ListTerminologies.md) – Use to list custom terminologies in your account\. |  `translate:ListTerminologies`  | \* | 
| [StartTextTranslationJob](API_StartTextTranslationJob.md) \- Use to start an [asynchronous batch translation job\.](async.md)  |  `translate:StartTextTranslationJob` You also need to give an IAM role read permission to the Amazon S3 folder that contains your input files, and read and write permissions to the folder that will contain your output files\.  | \* | 
| [DescribeTextTranslationJob](API_DescribeTextTranslationJob.md) \- Use to get details on a batch translation job\. | `translate:DescribeTextTranslationJob` | \* | 
| [ListTextTranslationJobs](API_ListTextTranslationJobs.md) \- Use to list all batch translation jobs in your account in the current Region\. | translate:ListTextTranslationJobs | \* | 
| [StopTextTranslationJob](API_StopTextTranslationJob.md) \- Use to stop a batch translation job\. | translate:StopTextTranslationJob | \* | 
