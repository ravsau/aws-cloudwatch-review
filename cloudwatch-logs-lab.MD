## Send Apache logs to CloudWatch from Amazon EC2

Before we start: 
- install the httpd web server.
- Attach a role with cloudWatch write access to the ec2 instance

**Step 1-3 are optional if you’re using an Amazon Linux AMI. They come with Cloud watch agent installed.

Step 1: Download CloudWatch agent –
```console
$ wget https://s3.amazonaws.com/amazoncloudwatch-pagent/linux/amd64/latest/AmazonCloudWatchAgent.zip
```

Step 2: Unzip the downloaded fille—
```console
$ unzip AmazonCloudWatchAgent.zip
```

Step 3: Install the agent
```console
$ sudo ./install.sh
```

Step 4: Configure the Cloudwatch Agent 
```console
 $ sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
```

Step 5: Choose from different setting that you are prompted. In the log file path specify:
/etc/httpd/logs/access_log

Step 6: Start CloudWatch Agent 
```console
/opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c file://opt/aws/amazon-cloudwatch-agent/bin/config.json -s

```

You can change the config file here if needed:
/opt/aws/amazon-cloudwatch-agent/bin/config.json


Reference: https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/create-cloudwatch-agent-configuration-file-wizard.html


