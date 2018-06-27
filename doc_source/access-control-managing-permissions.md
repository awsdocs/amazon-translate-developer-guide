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
                "translate:TranslateText",
                "comprehend:DetectDominantLanguage"
             ],   
            "Resource": "*"
        }
    ]
}
```

The policy has two statements\. The first grants permissions to use the `TranslateText` action\. The second grants permissions to the Amazon Comprehend `DetectDominantLanguage` operation to enable automatic language detection\.

The policy doesn't specify the `Principal` element because you don't specify the principal who gets the permissions in an identity\-based policy\. When you attach a policy to a user, the user is the implicit principal\. When you attach a permissions policy to an IAM role, the principal identified in the role's trust policy gets the permissions\. 

For a table of the Amazon Translate API actions and the resources that they apply to, see [Amazon Translate API Permissions: Actions, Resources, and Conditions Reference](translate-api-permissions-ref.md)\.