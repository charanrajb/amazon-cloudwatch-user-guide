# Using Service\-Linked Roles for CloudWatch Application Insights for \.NET and SQL Server<a name="CHAP_using-service-linked-roles-appinsights"></a>

CloudWatch Application Insights uses AWS Identity and Access Management \(IAM\)[ service\-linked roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role)\. A service\-linked role is a unique type of IAM role that is linked directly to CloudWatch Application Insights for \.NET and SQL Server\. Service\-linked roles are predefined by CloudWatch Application Insights for \.NET and SQL Server and include all the permissions that the service requires to call other AWS services on your behalf\. 

A service\-linked role makes setting up CloudWatch Application Insights for \.NET and SQL Server easier because you don’t have to manually add the necessary permissions\. CloudWatch Application Insights for \.NET and SQL Server defines the permissions of its service\-linked roles, and unless defined otherwise, only CloudWatch Application Insights for \.NET and SQL Server can assume its roles\. The defined permissions include the trust policy and the permissions policy, and that permissions policy cannot be attached to any other IAM entity\.

For information about other services that support service\-linked roles, see [AWS Services That Work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html) and look for the services that have **Yes **in the **Service\-Linked Role** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\.

## Service\-Linked Role Permissions for CloudWatch Application Insights for \.NET and SQL Server<a name="service-linked-role-permissions"></a>

CloudWatch Application Insights for \.NET and SQL Server uses the service\-linked role named **ApplicationInsights\-role** – Application Insights uses this role to perform operations such as analyzing the Resource Groups of the customer, creating CloudFormation stacks to create alarms on metrics, and to configure the CloudWatch Agent on EC2 instances\.

The role permissions policy allows CloudWatch Application Insights for \.NET and SQL Server to complete the following actions on all resources:
+ `cloudwatch:DescribeAlarmHistory`
+  `cloudwatch:DescribeAlarms`
+  `cloudwatch:GetMetricData`
+ `cloudwatch:ListMetrics`
+ `cloudwatch:PutMetricAlarm`
+ `cloudwatch:DeleteAlarms`
+ `logs:GetLogEvents` 
+  `logs:DescribeLogStreams`
+  `logs:DescribeLogGroup`
+ `events:DescribeRule` 
+ `tag:GetResources` 
+ `resource-groups:ListGroupResources` 
+ `resource-groups:GetGroupQuery` 
+ `elasticloadbalancing:DescribeLoadBalancers` 
+ `elasticloadbalancing:DescribeTargetGroups` 
+ `elasticloadbalancing:DescribeTargetHealth` 
+ `Autoscaling:DescribeAutoScalingGroups` 

You must configure permissions to allow an IAM entity \(such as a user, group, or role\) to create, edit, or delete a service\-linked role\. For more information, see [Service\-Linked Role Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#service-linked-role-permissions) in the *IAM User Guide*\.

## Creating a Service\-Linked Role for CloudWatch Application Insights for \.NET and SQL Server<a name="create-service-linked-role"></a>

You don't need to manually create a service\-linked role\. When you create a new Application Insights application in the AWS Management Console, CloudWatch Application Insights for \.NET and SQL Server creates the service\-linked role for you\. 

If you delete this service\-linked role, and then need to create it again, you can use the same process to recreate the role in your account\. When you create a new Application Insights application, CloudWatch Application Insights for \.NET and SQL Server creates the service\-linked role for you again\. 

## Editing a Service\-Linked Role for CloudWatch Application Insights for \.NET and SQL Server<a name="edit-slr"></a>

CloudWatch Application Insights for \.NET and SQL Server does not allow you to edit the ApplicationInsights\-role service\-linked role\. After you create a service\-linked role, you cannot change the name of the role because various entities might reference the role\. However, you can edit the description of the role using IAM\. For more information, see [Editing a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Deleting a Service\-Linked Role for CloudWatch Application Insights for \.NET and SQL Server<a name="delete-service-linked-role"></a>

If you no longer need to use a feature or service that requires a service\-linked role, we recommend that you delete that role\. That way you don’t have an unused entity that is not actively monitored or maintained\. However, you must delete all applications in Application Insights before you can manually delete it\.

**Note**  
If the CloudWatch Application Insights for \.NET and SQL Server service is using the role when you try to delete the resources, then the deletion might fail\. If that happens, wait for a few minutes and try the operation again\.

**To delete CloudWatch Application Insights for \.NET and SQL Server resources used by the ApplicationInsights\-role**
+ Delete all of your CloudWatch Application Insights for \.NET and SQL Server applications\. For more information, see "Deleting Your Application\(s\)" in the CloudWatch Application Insights for \.NET and SQL Server User Guide\. 

**To manually delete the service\-linked role using IAM**

Use the IAM console, the AWS CLI, or the AWS API to delete the ApplicationInsights\-role service\-linked role\. For more information, see [Deleting a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide*\.

## Supported Regions for CloudWatch Application Insights for \.NET and SQL Server Service\-Linked Roles<a name="slr-regions"></a>

CloudWatch Application Insights for \.NET and SQL Server supports using service\-linked roles in all of the regions where the service is available\.


****  

| Region name | Region identity | Support in CloudWatch Application Insights for \.NET and SQL Server | 
| --- | --- | --- | 
| US East \(N\. Virginia\) | us\-east\-1 | Yes | 
| US East \(Ohio\) | us\-east\-2 | No | 
| US West \(N\. California\) | us\-west\-1 | No | 
| US West \(Oregon\) | us\-west\-2 | No | 
| Asia Pacific \(Mumbai\) | ap\-south\-1 | No | 
| Asia Pacific \(Osaka\-Local\) | ap\-northeast\-3 | No | 
| Asia Pacific \(Seoul\) | ap\-northeast\-2 | No | 
| Asia Pacific \(Singapore\) | ap\-southeast\-1 | No | 
| Asia Pacific \(Sydney\) | ap\-southeast\-2 | No | 
| Asia Pacific \(Tokyo\) | ap\-northeast\-1 | No | 
| Canada \(Central\) | ca\-central\-1 | No | 
| EU \(Frankfurt\) | eu\-central\-1 | No | 
| EU \(Ireland\) | eu\-west\-1 | No | 
| EU \(London\) | eu\-west\-2 | No | 
| EU \(Paris\) | eu\-west\-3 | No | 
| South America \(São Paulo\) | sa\-east\-1 | No | 
| AWS GovCloud \(US\) | us\-gov\-west\-1 | No | 