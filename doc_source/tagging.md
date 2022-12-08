# Tagging your resources<a name="tagging"></a>

A tag is metadata that you can associate with an Amazon Translate resource\. A tag consists of a key\-value pair\. You can add tags to **Parallel Data** and **Custom Terminology** resources\.

Tags have two major functions: organizing your resources and providing tag\-based access control\. You can add tags to a resource and then create IAM policies to allow or restrict access to the resource based on its tags\.

A policy can allow or disallow an operation based on the tags provided in your request \(request\-tags\) or tags associated with the resource you're calling \(resource\-tags\)\. For more information on using tags with IAM, see [Controlling access using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) in the *IAM User Guide*\.

Considerations for using tags with Amazon Translate:
+ You can add up to 50 user tags per resource\. 
+ You can add tags when you create the resource, or any time after you create it\.
+  A tag *key* is a required field but a tag *value* is optional\.
+ Tags don't have to be unique between resources, but the tags for a given resource must have unique keys\.
+ Tag keys and values are case sensitive\.
+ A tag key can have a maximum of 128 characters; a tag value can have a maximum of 256 characters\.
+ AWS system tags start with prefix `aws:` in the tag key or value\. You can't add, edit, or delete tag names or values with this prefix\. System tags are not included in your tags quota per resource\.

**Note**  
If you plan to use your tagging schema across multiple AWS services and resources, remember that other services may have different requirements for allowed characters\.

**Topics**
+ [Tagging a new resource](tagging-newtags.md)
+ [Viewing, updating, and deleting tags associated with a resource](tagging-existingtags.md)