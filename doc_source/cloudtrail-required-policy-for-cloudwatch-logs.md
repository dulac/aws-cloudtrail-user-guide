# Role Policy Document for CloudTrail to Use CloudWatch Logs for Monitoring<a name="cloudtrail-required-policy-for-cloudwatch-logs"></a>

This section describes the IAM policy required for the CloudTrail role to send log events to CloudWatch Logs\. You can attach a policy document to a role when you configure CloudTrail to send events, as described in [Sending Events to CloudWatch Logs](send-cloudtrail-events-to-cloudwatch-logs.md)\. You can also create a role using IAM\. For more information, see [Creating a Role for an AWS Service \(AWS Management Console\)](http://docs.aws.amazon.com/IAM/latest/UserGuide/create-role-xacct.html) or [Creating a Role \(CLI and API\)](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_CreateRole_CLIAPI.html)\.

The following example policy document contains the permissions required to create a CloudWatch log stream in the log group that you specify and to deliver CloudTrail events to that log stream in the US East \(Ohio\) region\. \(This is the default policy for the default IAM role `CloudTrail_CloudWatchLogs_Role`\.\)

```
{
  "Version": "2012-10-17",
  "Statement": [
    {

      "Sid": "AWSCloudTrailCreateLogStream2014110",
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogStream"
      ],
      "Resource": [
        "arn:aws:logs:us-east-2:accountID:log-group:log_group_name:log-stream:CloudTrail_log_stream_name_prefix*"
      ]

    },
    {
      "Sid": "AWSCloudTrailPutLogEvents20141101",
      "Effect": "Allow",
      "Action": [
        "logs:PutLogEvents"
      ],
      "Resource": [
        "arn:aws:logs:us-east-2:accountID:log-group:log_group_name:log-stream:CloudTrail_log_stream_name_prefix*"
      ]
    }
  ]
}
```
