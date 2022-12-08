# How Amazon Translate works with IAM<a name="security_iam_service-with-iam"></a>

You can manage access to Amazon Translate operations and resources with AWS Identity and Access Management\. Before you use AWS Identity and Access Management \(IAM\) to manage access to Amazon Translate, you should understand which IAM features are available to use with Amazon Translate\. To get a high\-level view of how Amazon Translate and other AWS services work with IAM, see [AWS services that work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html) in the *IAM User Guide*\.

**Topics**
+ [Amazon Translate identity\-based policies](#access-control-managing-permissions)
+ [Amazon Translate resource\-based policies](#security_iam_service-with-iam-resource-based-policies)
+ [Authorization based on Amazon Translate tags](#security_iam_service-with-iam-tags)
+ [Amazon Translate IAM roles](#security_iam_service-with-iam-roles)

## Amazon Translate identity\-based policies<a name="access-control-managing-permissions"></a>

With IAM identity\-based policies, you can specify allowed or denied actions and resources as well as the conditions under which actions are allowed or denied\. Amazon Translate supports specific actions, resources, and condition keys\. To learn about all of the elements that you use in a JSON policy, see [IAM JSON policy elements reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html) in the *IAM User Guide*\.

### Actions<a name="security_iam_service-with-iam-id-based-policies-actions"></a>

Administrators can use AWS JSON policies to specify who has access to what\. That is, which **principal** can perform **actions** on what **resources**, and under what **conditions**\.

The `Action` element of a JSON policy describes the actions that you can use to allow or deny access in a policy\. Policy actions usually have the same name as the associated AWS API operation\. There are some exceptions, such as *permission\-only actions* that don't have a matching API operation\. There are also some operations that require multiple actions in a policy\. These additional actions are called *dependent actions*\.

Include actions in a policy to grant permissions to perform the associated operation\.



Policy actions in Amazon Translate use the following prefix before the action: `translate:`\. For example, to grant someone permission to perform a translation with the Amazon Translate `TranslateText` API operation, log in as an admin and include the `translate:TranslateText` action in their policy\. Policy statements must include either an `Action` or `NotAction` element\. Amazon Translate defines its own set of actions that describe tasks that you can perform with this service\. To see a list of Amazon Translate actions, see [Actions defined by Amazon Translate](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazontranslate.html#amazontranslate-actions-as-permissions) in the *IAM User Guide*\.

To specify multiple actions in a single statement, separate them with commas as follows:

```
"Action": [
      "translate:action1",
      "translate:action2"
```

### Resources<a name="security_iam_service-with-iam-id-based-policies-resources"></a>

Amazon Translate doesn't support specifying resource Amazon Resource Names \(ARNs\) in a policy\.

### Condition keys<a name="security_iam_service-with-iam-id-based-policies-conditionkeys"></a>

Amazon Translate doesn't provide any service\-specific condition keys, but it does support using some global condition keys\. To see all AWS global condition keys, see [AWS Global condition context keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\.

Administrators can use AWS JSON policies to specify who has access to what\. That is, which **principal** can perform **actions** on what **resources**, and under what **conditions**\.

The `Condition` element \(or `Condition` *block*\) lets you specify conditions in which a statement is in effect\. The `Condition` element is optional\. You can create conditional expressions that use [condition operators](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition_operators.html), such as equals or less than, to match the condition in the policy with values in the request\. 

If you specify multiple `Condition` elements in a statement, or multiple keys in a single `Condition` element, AWS evaluates them using a logical `AND` operation\. If you specify multiple values for a single condition key, AWS evaluates the condition using a logical `OR` operation\. All of the conditions must be met before the statement's permissions are granted\.

 You can also use placeholder variables when you specify conditions\. For example, you can grant an IAM user permission to access a resource only if it is tagged with their IAM user name\. For more information, see [IAM policy elements: variables and tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html) in the *IAM User Guide*\. 

AWS supports global condition keys and service\-specific condition keys\. To see all AWS global condition keys, see [AWS global condition context keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\.

### Examples<a name="security_iam_service-with-iam-id-based-policies-examples"></a>



To see examples of Amazon Translate identity\-based policies, see [Amazon Translate identity\-based policy examples](security_iam_id-based-policy-examples.md)\.

## Amazon Translate resource\-based policies<a name="security_iam_service-with-iam-resource-based-policies"></a>

Amazon Translate doesn't support resource\-based policies\.

## Authorization based on Amazon Translate tags<a name="security_iam_service-with-iam-tags"></a>

Amazon Translate supports tags for **Parallel Data** and **Import Terminology**\.

You can use the tags to provide tag\-based access control\. You add tags to a resource and then create IAM policies to allow or restrict access to the resource based on its tags\. For more information on using tags with IAM, see [Controlling access using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) in the *IAM User Guide*\.

For details about the Amazon Translate resource types, see [ Actions, resources, and condition keys for Amazon Translate ](https://docs.aws.amazon.com/service-authorization/latest/reference/list_amazontranslate.html) in the *Service Authorization Reference*\. 

## Amazon Translate IAM roles<a name="security_iam_service-with-iam-roles"></a>

An [IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) is an entity within your AWS account that has specific permissions\.

### Using temporary credentials with Amazon Translate<a name="security_iam_service-with-iam-roles-tempcreds"></a>

You can use temporary credentials to sign in with federation, assume an IAM role, or to assume a cross\-account role\. You obtain temporary security credentials by calling AWS Security Token Service \(AWS STS\) API operations such as [AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) or [GetFederationToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)\. 

Amazon Translate supports using temporary credentials\. 

### Service\-linked roles<a name="security_iam_service-with-iam-roles-service-linked"></a>

[Service\-linked roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) allow AWS services to access resources in other services to complete an action on your behalf\. Service\-linked roles appear in your IAM account and are owned by the service\. An IAM administrator can view, but not edit\. the permissions for service\-linked roles\.

Amazon Translate doesn't support service\-linked roles\.