# Working with Key Policies<a name="programming-key-policies"></a>

The examples in this topic use the AWS KMS API to view and change the key policies of AWS KMS customer master keys \(CMKs\)\. For details about how to use key policies and IAM policies to manage access to your CMKs, see [Authentication and Access Control for AWS KMS](control-access.md)\.

**Topics**
+ [Listing Key Policy Names](#list-policies)
+ [Getting a Key Policy](#get-policy)
+ [Setting a Key Policy](#put-policy)

## Listing Key Policy Names<a name="list-policies"></a>

To get the names of key policies for a customer master key, use the [ListKeyPolicies](https://docs.aws.amazon.com/kms/latest/APIReference/API_ListKeyPolicies.html) operation\. The only key policy name it returns is **default**\.

This example uses the `kmsClient` client object that you created in [Creating a Client](programming-client.md)\.

------
#### [ Java ]

For details about the Java implementation, see the [listKeyPolicies method](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/kms/AWSKMSClient.html#listKeyPolicies-com.amazonaws.services.kms.model.ListKeyPoliciesRequest-) in the *AWS SDK for Java API Reference*\.

```
// List key policies
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
String keyId = "arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab";

ListKeyPoliciesRequest req = new ListKeyPoliciesRequest().withKeyId(keyId);
ListKeyPoliciesResult result = kmsClient.listKeyPolicies(req);
```

------
#### [ C\# ]

For details, see the [ListKeyPolicies method](https://docs.aws.amazon.com/sdkfornet/v3/apidocs/items/KeyManagementService/MKeyManagementServiceListKeyPoliciesListKeyPoliciesRequest.html) in the *AWS SDK for \.NET*\.

```
// List key policies
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
String keyId = "arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab";

ListKeyPoliciesRequest listKeyPoliciesRequest = new ListKeyPoliciesRequest()
{
    KeyId = keyId
};
ListKeyPoliciesResponse listKeyPoliciesResponse = kmsClient.ListKeyPolicies(listKeyPoliciesRequest);
```

------
#### [ Python ]

For details, see the [list\_key\_policies method](http://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/kms.html#KMS.Client.list_key_policies) in the AWS SDK for Python \(Boto 3\)\.

```
# List key policies

# Replace the following fictitious CMK ARN with a valid CMK ID or ARN
key_id = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab'

response = kms_client.list_key_policies(
    KeyId=key_id
)
```

------
#### [ Ruby ]

For details, see the [list\_key\_policies](https://docs.aws.amazon.com/sdk-for-ruby/v3/api/Aws/KMS/Client.html#list_key_policies-instance_method) instance method in the [AWS SDK for Ruby](https://docs.aws.amazon.com/sdk-for-ruby/v3/api/Aws/KMS.html)\.

```
# List key policies

# Replace the following fictitious CMK ARN with a valid CMK ID or ARN
keyId = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab'

response = kmsClient.list_key_policies({
  key_id: keyId
})
```

------
#### [ PHP ]

For details, see the [ListKeyPolicies method](https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-kms-2014-11-01.html#listkeypolicies) in the *AWS SDK for PHP*\.

```
// List key policies
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
$keyId = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab';

$result = $KmsClient->listKeyPolicies([
    'KeyId' => $keyId
]);
```

------
#### [ Node\.js ]

For details, see the [listKeyPolicies property](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/KMS.html#listKeyPolicies-property) in the *AWS SDK for JavaScript in Node\.js*\.

```
// List key policies
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
const KeyId = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab';

kmsClient.listKeyPolicies({ KeyId }, (err, data) => {
  ...
});
```

------

## Getting a Key Policy<a name="get-policy"></a>

To get the key policy for a customer master key, use the [GetKeyPolicy](https://docs.aws.amazon.com/kms/latest/APIReference/API_GetKeyPolicy.html) operation\.

GetKeyPolicy requires a policy name\. The only valid policy name is **default**\.

This example uses the `kmsClient` client object that you created in [Creating a Client](programming-client.md)\.

------
#### [ Java ]

For details, see the [getKeyPolicy method](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/kms/AWSKMSClient.html#getKeyPolicy-com.amazonaws.services.kms.model.GetKeyPolicyRequest-) in the *AWS SDK for Java API Reference*\.

```
// Get the policy for a CMK
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
String keyId = "arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab";
String policyName = "default";

GetKeyPolicyRequest req = new GetKeyPolicyRequest().withKeyId(keyId).withPolicyName(policyName);
GetKeyPolicyResult result = kmsClient.getKeyPolicy(req);
```

------
#### [ C\# ]

For details, see the [GetKeyPolicy method](https://docs.aws.amazon.com/sdkfornet/v3/apidocs/items/KeyManagementService/MKeyManagementServiceGetKeyPolicyGetKeyPolicyRequest.html) in the *AWS SDK for \.NET*\.

```
// Get the policy for a CMK
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
String keyId = "arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab";
String policyName = "default";

GetKeyPolicyRequest getKeyPolicyRequest = new GetKeyPolicyRequest()
{
    KeyId = keyId,
    PolicyName = policyName
};
GetKeyPolicyResponse getKeyPolicyResponse = kmsClient.GetKeyPolicy(getKeyPolicyRequest);
```

------
#### [ Python ]

For details, see the [get\_key\_policy method](http://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/kms.html#KMS.Client.get_key_policy) in the AWS SDK for Python \(Boto 3\)\.

```
# Get the policy for a CMK

# Replace the following fictitious CMK ARN with a valid CMK ID or ARN
key_id = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab'
policy_name = 'default'

response = kms_client.get_key_policy(
    KeyId=key_id,
    PolicyName=policy_name
)
```

------
#### [ Ruby ]

For details, see the [get\_key\_policy](https://docs.aws.amazon.com/sdk-for-ruby/v3/api/Aws/KMS/Client.html#get_key_policy-instance_method) instance method in the [AWS SDK for Ruby](https://docs.aws.amazon.com/sdk-for-ruby/v3/api/Aws/KMS.html)\.

```
# Get the policy for a CMK

# Replace the following fictitious CMK ARN with a valid CMK ID or ARN
keyId = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab'
policyName = 'default'

response = kmsClient.get_key_policy({
  key_id: keyId,
  policy_name: policyName
})
```

------
#### [ PHP ]

For details, see the [GetKeyPolicy method](https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-kms-2014-11-01.html#getkeypolicy) in the *AWS SDK for PHP*\.

```
// Get the policy for a CMK
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
$keyId = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab';
$policyName = "default";

$result = $KmsClient->getKeyPolicy([
    'KeyId' => $keyId, 
    'PolicyName' => $policyName
]);
```

------
#### [ Node\.js ]

For details, see the [getKeyPolicy property](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/KMS.html#getKeyPolicy-property) in the *AWS SDK for JavaScript in Node\.js*\.

```
// Get the policy for a CMK
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
const KeyId = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab';
const PolicyName = 'default';
kmsClient.getKeyPolicy({ KeyId, PolicyName }, (err, data) => {
  ...
});
```

------

## Setting a Key Policy<a name="put-policy"></a>

To establish or change a key policy for a CMK, use the [PutKeyPolicy](https://docs.aws.amazon.com/kms/latest/APIReference/API_PutKeyPolicy.html) operation\.

PutKeyPolicy requires a policy name\. The only valid policy name is **default**\.

This example uses the `kmsClient` client object that you created in [Creating a Client](programming-client.md)\.

------
#### [ Java ]

For details, see the [putKeyPolicy method](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/kms/AWSKMSClient.html#putKeyPolicy-com.amazonaws.services.kms.model.PutKeyPolicyRequest-) in the *AWS SDK for Java API Reference*\.

```
// Set a key policy for a CMK
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
String keyId = "arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab";
String policyName = "default";
String policy = "{" +
                "  \"Version\": \"2012-10-17\"," +
                "  \"Statement\": [{" +
                "    \"Sid\": \"Allow access for ExampleUser\"," +
                "    \"Effect\": \"Allow\"," +
                // Replace the following user ARN with one for a real user.
                "    \"Principal\": {\"AWS\": \"arn:aws:iam::111122223333:user/ExampleUser\"}," +
                "    \"Action\": [" +
                "      \"kms:Encrypt\"," +
                "      \"kms:GenerateDataKey*\"," +
                "      \"kms:Decrypt\"," +
                "      \"kms:DescribeKey\"," +
                "      \"kms:ReEncrypt*\"" +
                "    ]," +
                "    \"Resource\": \"*\"" +
                "  }]" +
                "}";
                
PutKeyPolicyRequest req = new PutKeyPolicyRequest().withKeyId(keyId).withPolicy(policy).withPolicyName(policyName);
kmsClient.putKeyPolicy(req);
```

------
#### [ C\# ]

For details, see the [PutKeyPolicy method](https://docs.aws.amazon.com/sdkfornet/v3/apidocs/items/KeyManagementService/MKeyManagementServicePutKeyPolicyPutKeyPolicyRequest.html) in the *AWS SDK for \.NET*\.

```
// Set a key policy for a CMK
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
String keyId = "arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab";
String policyName = "default";
String policy = "{" +
                "  \"Version\": \"2012-10-17\"," +
                "  \"Statement\": [{" +
                "    \"Sid\": \"Allow access for ExampleUser\"," +
                "    \"Effect\": \"Allow\"," +
                // Replace the following user ARN with one for a real user.
                "    \"Principal\": {\"AWS\": \"arn:aws:iam::111122223333:user/ExampleUser\"}," +
                "    \"Action\": [" +
                "      \"kms:Encrypt\"," +
                "      \"kms:GenerateDataKey*\"," +
                "      \"kms:Decrypt\"," +
                "      \"kms:DescribeKey\"," +
                "      \"kms:ReEncrypt*\"" +
                "    ]," +
                "    \"Resource\": \"*\"" +
                "  }]" +
                "}";
                
PutKeyPolicyRequest putKeyPolicyRequest = new PutKeyPolicyRequest()
{
    KeyId = keyId,
    Policy = policy,
    PolicyName = policyName
};
kmsClient.PutKeyPolicy(putKeyPolicyRequest);
```

------
#### [ Python ]

For details, see the [put\_key\_policy method](http://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/kms.html#KMS.Client.put_key_policy) in the AWS SDK for Python \(Boto 3\)\.

```
# Set a key policy for a CMK

# Replace the following fictitious CMK ARN with a valid CMK ID or ARN
key_id = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab'
policy_name = 'default'
policy = """
{
    "Version": "2012-10-17",
    "Statement": [{
        "Sid": "Allow access for ExampleUser",
        "Effect": "Allow",
        "Principal": {"AWS": "arn:aws:iam::111122223333:user/ExampleUser"},
        "Action": [
            "kms:Encrypt",
            "kms:GenerateDataKey*",
            "kms:Decrypt",
            "kms:DescribeKey",
            "kms:ReEncrypt*"
        ],
        "Resource": "*"
    }]
}"""

response = kms_client.put_key_policy(
    KeyId=key_id,
    Policy=policy,
    PolicyName=policy_name
)
```

------
#### [ Ruby ]

For details, see the [put\_key\_policy](https://docs.aws.amazon.com/sdk-for-ruby/v3/api/Aws/KMS/Client.html#put_key_policy-instance_method) instance method in the [AWS SDK for Ruby](https://docs.aws.amazon.com/sdk-for-ruby/v3/api/Aws/KMS.html)\.

```
# Set a key policy for a CMK

# Replace the following fictitious CMK ARN with a valid CMK ID or ARN
keyId = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab'
policyName = 'default'
policy = "{\n
\n    "Version": "2012-10-17",
\n    "Statement": [{
\n        "Sid": "Allow access for ExampleUser",
\n        "Effect": "Allow",
\n        "Principal": {"AWS": "arn:aws:iam::111122223333:user/ExampleUser"},
\n        "Action": [
\n            "kms:Encrypt",
\n            "kms:GenerateDataKey*",
\n            "kms:Decrypt",
\n            "kms:DescribeKey",
\n            "kms:ReEncrypt*"
\n        ],
\n        "Resource": "*"
\n    }]
\n}\n"

response = kmsClient.put_key_policy({
  key_id: keyId,
  policy: policy,
  policy_name: policyName
})
```

------
#### [ PHP ]

For details, see the [PutKeyPolicy method](https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-kms-2014-11-01.html#putkeypolicy) in the *AWS SDK for PHP*\.

```
// Set a key policy for a CMK
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
$keyId = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab';
$policyName = "default";

$result = $KmsClient->putKeyPolicy([
    'KeyId' => $keyId, 
    'PolicyName' => $policyName, 
    'Policy' => '{ 
        "Version": "2012-10-17", 
        "Id": "custom-policy-2016-12-07", 
        "Statement": [ 
            { "Sid": "Enable IAM User Permissions", 
            "Effect": "Allow", 
            "Principal": 
               { "AWS": "arn:aws:iam::111122223333:user/root" }, 
            "Action": [ "kms:*" ], 
            "Resource": "*" }, 
            { "Sid": "Enable IAM User Permissions", 
            "Effect": "Allow", 
            "Principal":
               { "AWS": "arn:aws:iam::111122223333:user/ExampleUser" }, 
            "Action": [
                "kms:Encrypt*",
                "kms:GenerateDataKey*",
                "kms:Decrypt*",
                "kms:DescribeKey*",
                "kms:ReEncrypt*"
            ], 
            "Resource": "*" }
        ]
    } ' 
]);
```

------
#### [ Node\.js ]

For details, see the [putKeyPolicy property](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/KMS.html#putKeyPolicy-property) in the *AWS SDK for Node\.js*\.

```
// Set a key policy for a CMK
//
// Replace the following fictitious CMK ARN with a valid CMK ID or ARN
const KeyId = 'arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab';
const PolicyName = 'default';
const Policy = `{
    "Version": "2012-10-17",
    "Id": "custom-policy-2016-12-07",
    "Statement": [
        {
            "Sid": "Enable IAM User Permissions",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::111122223333:root"
            },
            "Action": "kms:*",
            "Resource": "*"
        },
        {
            "Sid": "Enable IAM User Permissions",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::111122223333:user/ExampleUser"
            },
            "Action": [
                "kms:Encrypt*",
                "kms:GenerateDataKey*",
                "kms:Decrypt*",
                "kms:DescribeKey*",
                "kms:ReEncrypt*"
            ],
            "Resource": "*"
        } 
    ]
}`; // The key policy document
  
kmsClient.putKeyPolicy({ KeyId, Policy, PolicyName }, (err, data) => {
  ...
});
```

------