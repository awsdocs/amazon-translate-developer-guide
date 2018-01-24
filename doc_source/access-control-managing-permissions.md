# Using Identity\-Based Polices \(IAM Policies\) for Amazon Translate<a name="access-control-managing-permissions"></a>

This topic provides examples of identity\-based policies that demonstrate how an account administrator can attach permissions policies to IAM identities \(that is, users, groups, and roles\) and thereby grant permissions to perform Amazon Translate actions\. 

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
                "translate:TranslateText"
             ],   
            "Resource": "*"
        }
    ]
}
```

The policy has one statement that grants permission to use the `TranslateText` action\.

The policy doesn't specify the `Principal` element because you don't specify the principal who gets the permission in an identity\-based policy\. When you attach a policy to a user, the user is the implicit principal\. When you attach a permissions policy to an IAM role, the principal identified in the role's trust policy gets the permissions\. 

For a table showing all of the Amazon Translate API actions and the resources that they apply to, see [Amazon Translate API Permissions: Actions, Resources, and Conditions Reference](translate-api-permissions-ref.md)\.