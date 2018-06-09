Custom Metrics in Amazon CloudWatch: Memory Utilization and Disk Usage
 

[![View this lab as a video](https://i.ytimg.com/vi/bgRt3kiNt_Q/maxresdefault.jpg)](https://www.youtube.com/watch?v=bgRt3kiNt_Q&t=454s) 
  
 
Step 1: Launch a Linux Instance

Step 2: Ensure that the scripts have permission to perform CloudWatch operations. Create cloudwatch full access role and attach to the EC2
 
Step 3: Install Perl files
```console
$ sudo yum install perl-Switch perl-DateTime perl-Sys-Syslog perl-LWP-Protocol-https –y
```
 
Step 4: download monitoring scripts in a folder
```console 
curl http://aws-cloudwatch.s3.amazonaws.com/downloads/CloudWatchMonitoringScripts-1.2.1.zip -O
```
 
Step 5:Unzip
```console
unzip CloudWatchMonitoringScripts-1.2.1.zip
``` 
 
Step 6: 
```console
cd aws-scripts-mon
``` 
 
Step7:
```console
mon-put-instance-data.pl
```

This script collects memory, swap, and disk space utilization data on the current system. It then makes a remote call to Amazon CloudWatch to report the collected data as custom metrics.
To collect all available memory metrics and send them to CloudWatch
 
```console
./mon-put-instance-data.pl --mem-util --mem-used-incl-cache-buff --mem-used --mem-avail
```
 
Step 8:
To set a cron schedule for metrics reported to CloudWatch:
Start editing the crontab using the following command:
```console 
$ crontab –e
```
Add the following command to report memory and disk space utilization to CloudWatch every one minute:
 
Copy and paste this:
* * * * * ~/aws-scripts-mon/mon-put-instance-data.pl --mem-used-incl-cache-buff --mem-util --disk-space-util --disk-path=/ --from-cron
 
** Use */5 if you want to do it every 5 minutes.
 
Viewing Your Custom Metrics in the Console

After you successfully run the mon-put-instance-data.pl script, you can view your custom metrics in the Amazon CloudWatch console.
 
1. Open the CloudWatch console at https://console.aws.amazon.com/cloudwatch/.
2. Choose View Metrics.
3. For Viewing, your custom metrics posted by the script are displayed with the prefix System/Linux.
 
 
Reference:
 
http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/mon-scripts.html
 
 
