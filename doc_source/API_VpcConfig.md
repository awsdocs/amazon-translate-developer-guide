# VpcConfig<a name="API_VpcConfig"></a>

Provides information about an EC2 instance's Virtual Private Cloud \(VPC\) configuration\.

## Contents<a name="API_VpcConfig_Contents"></a>

 **SecurityGroupIds**   <a name="Translate-Type-VpcConfig-SecurityGroupIds"></a>
The identifiers of the security groups to which the calling EC2 instance belongs\.  
Type: Array of strings  
Array Members: Minimum number of 1 item\. Maximum number of 5 items\.  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `[-0-9a-zA-Z]+`   
Required: Yes

 **Subnets**   <a name="Translate-Type-VpcConfig-Subnets"></a>
The identifiers of the calling EC2 instance's subnets\.  
Type: Array of strings  
Array Members: Minimum number of 1 item\. Maximum number of 16 items\.  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `[-0-9a-zA-Z]+`   
Required: Yes

## See Also<a name="API_VpcConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/translate-2017-07-01/VpcConfig) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/translate-2017-07-01/VpcConfig) 
+  [AWS SDK for Go \- Pilot](https://docs.aws.amazon.com/goto/SdkForGoPilot/translate-2017-07-01/VpcConfig) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/translate-2017-07-01/VpcConfig) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/translate-2017-07-01/VpcConfig) 