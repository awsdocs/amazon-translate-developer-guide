# Amazon Translate API Permissions: Actions, Resources, and Conditions Reference<a name="translate-api-permissions-ref"></a>

Use the following table as a reference when setting up [Access Control](auth-and-access-control.md#access-control) and writing a permissions policy that you can attach to an IAM identity \(an identity\-based policy\)\. The list includes each Amazon Translate API operation, the corresponding action for which you can grant permissions to perform the action, and the AWS resource for which you can grant the permissions\. You specify the actions in the policy's `Action` field, and you specify the resource value in the policy's `Resource` field\. 

To express conditions, you can use AWS\-wide condition keys in your Amazon Translate policies\. For a complete list of AWS\-wide keys, see [Available Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\. 

**Note**  
To specify an action, use the `translate:` prefix followed by the API operation name, for example, `translate:TranslateText`\.

If you see an expand arrow \(**↗**\) in the upper\-right corner of the table, you can open the table in a new window\. To close the window, choose the close button \(**X**\) in the lower\-right corner\.


**Amazon Translate API and Required Permissions for Actions**  

| Amazon Translate API Operations | Required Permissions \(API Actions\) | Resources | 
| --- | --- | --- | 
| [TranslateText](API_TranslateText.md) – Use to specify the source language  |  `translate:TranslateText`  | \* | 
| [TranslateText](API_TranslateText.md) – Use for automatic source language detection |  `translate:TranslateText` `comprehend:DetectDominantLanguage`  | \* | 
| [DeleteTerminology](API_DeleteTerminology.md) – Use for deleting a custom terminology from your account\. |  `translate:DeleteTerminology`  | \* | 
| [GetTerminology](API_GetTerminology.md) – Use for retrieving information on a custom terminology associated with your account\. |  `translate:GetTerminology` If the terminology uses KMS encryption, it also requires that the following permissions be set in the KMS key policy \(not an IAM policy\): `kms:Decrypt`  | \* | 
| [ImportTerminology](API_ImportTerminology.md) – Use for importing a custom terminology to your account\. |  `translate:ImportTerminology` If the terminology uses KMS encryption, it also requires that the following permissions be set in the KMS key policy \(not an IAM policy\): `kms:CreateGrant` `kms:DescribeKey` `kms:GenerateDataKey` `kms:RetireGrant`  | \* | 
| [ListTerminologies](API_ListTerminologies.md) – Use to list custom terminologies in your account\. |  `translate:ListTerminology`  | \* | 