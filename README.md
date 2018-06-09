
# A summary of Amazon CloudWatch 


![Example Cloudwatch Dashboard](https://raw.githubusercontent.com/ravsau/aws-cloudwatch-review/master/images/cloudwatch.png)

## What is Cloudwatch?
CloudWatch is the Monitoring Service in Amazon Web services which also allows you to react against events(AWS). 

## What can CloudWatch do? There are 3 distinct sub services in Cloudwatch. If you look at the navigation pane on the above image you can see that there are 4 sections ( Alarms, Events , Logs, Metrics). Metrics and alarms are linked and fall under the same IAM action group: 
                

1) **Cloudwatch (Core):** 
**Identity and access management(IAM) action group - cloudwatch:***
It monitors  resources in AWS like in the case of EC2 instances for CPU utilization, Network in/ outs and disk read/writes . At the same time you can use Custom Metrics to monitor more metrics like Memory Utilization.\

Cloudwatch can also set an alarm(eg your bill is above the monthly budget) and you can send a notification to notify and let you react.


2) **Cloudwatch Logs:**
**Identity and access management(IAM) action group - logs:***
With Cloudwatch logs you can send logs from your applications to Cloudwatch.\
Examples:
a) Send the logs of your AWS Lambda function to cloudwatch
b) Send the logs of your apache web-server to cloudwatch 

## Notice how it's different from Cloudwatch Metrics. Let me sumarize Cloudwatch Metrics and logs in 2 Pics

### Cloudwatch Metrics for AWS Lambda

![Lambda Metrics](https://raw.githubusercontent.com/ravsau/aws-cloudwatch-review/master/images/lambda-metrics.png)

### Cloudwatch Logs for AWS Lambda
![Lambda Logs](https://raw.githubusercontent.com/ravsau/aws-cloudwatch-review/master/images/lambda-logs.png)

3) **Cloudwatch Events :**
**Identity and access management(IAM) action group -events:***
With Cloudwatch Events you can do two things:\
a) Respond to event patterns that will trigger an action(Lambda function, SNS message, API calls)
b) Trigger an action in a cron like schedule.
