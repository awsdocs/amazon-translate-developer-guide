# Using Identity\-Based Policies \(IAM Policies\) for Amazon Translate<a name="access-control-managing-permissions"></a>

This topic provides an example of an identity\-based policy that demonstrate how an account administrator can attach permissions policies to IAM identities \(that is, users, groups, and roles\) to grant permissions to perform Amazon Translate actions\. 

**Important**  
Before you proceed, we recommend that you review [Overview of Managing Access Permissions to Your Amazon Translate Resources](access-control-overview.md)\. 

The following is the permissions policy required to use Amazon Translate and the Amazon Translate console:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "translate:*",
                "comprehend:DetectDominantLanguage",
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:ListMetrics"
             ],   
            "Resource": "*"

        }
    ]
}
```

The policy has four statements\. The first grants permissions to use the `TranslateText` action\. The second grants permissions to the Amazon Comprehend `DetectDominantLanguage` operation to enable automatic language detection\. The final two permissions grant permissions to use the Amazon Cloudwatch service to provide metrics support\.

The policy doesn't specify the `Principal` element because you don't specify the principal who gets the permissions in an identity\-based policy\. When you attach a policy to a user, the user is the implicit principal\. When you attach a permissions policy to an IAM role, the principal identified in the role's trust policy gets the permissions\. 

## KMS policies needed when using KMS CMKS with Amazon Translate custom terminologies\.<a name="kms-permissions"></a>

If you are using KMS CMKS with Amazon Translate custom terminologies, you may need one or more of the following permissions policies\.

If you want to be able to call ImportTerminology with a KMS CMK, you must have the following permissions in the KMS key policy \(as opposed to your IAM policy\):

```
{
    "Id": "key-consolepolicy-3",
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Allow access for use with Amazon Translate",
            "Effect": "Allow",
            "Principal": {
                "AWS": "IAM USER OR ROLE ARN"
            },
            "Action": [
                "kms:CreateGrant",
                "kms:DescribeKey",
                "kms:GenerateDataKey",
                "kms:RetireGrant"
            ],
            "Resource": "*"
        }
    ]
}
```

If you want to be able to call GetTerminology for a custom terminology that was imported with a KMS CMK, you must have at least the following permissions in the KMS key policy \(not in your IAM policy\):

```
{
    "Id": "key-consolepolicy-3",
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Allow access for use with Amazon Translate",
            "Effect": "Allow",
            "Principal": {
                "AWS": "IAM USER OR ROLE ARN"
            },
            "Action": [
                "kms:Decrypt"
            ],
            "Resource": "*"
        }
    ]
}
```

If you want to be able to call ListTerminologies or DeleteTermionlogy for a custom terminology that was imported with a KMS CMK, you don't need to have any special KMS permissions\.

If you want to have all possibilitiess covered, you should make sure you have at least the following permissions in the KMS key policy \(not in your IAM policy\):

```
{
    "Id": "key-consolepolicy-3",
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Allow access for use with Amazon Translate",
            "Effect": "Allow",
            "Principal": {
                "AWS": "IAM USER OR ROLE ARN"
            },
            "Action": [
                "kms:CreateGrant",
                "kms:DescribeKey",
                "kms:GenerateDataKey",
                "kms:RetireGrant",
                "kms:Decrypt"
            ],
            "Resource": "*"
        }
    ]
}
```

For a table of the Amazon Translate API actions and the resources that they apply to, see [Amazon Translate API Permissions: Actions, Resources, and Conditions Reference](translate-api-permissions-ref.md)\.