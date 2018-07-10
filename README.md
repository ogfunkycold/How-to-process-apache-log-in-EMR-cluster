# How to Process Apache Log in EMR Cluster

## Scenario
Analysis apache log to get the insight which knew what kind of visitor to your website. Also to get more information for setup the customization content for the visitors.

This lab introduces you to Amazon Elastic Mapreduce ([Amazon EMR](https://aws.amazon.com/emr/)) using the AWS Management Console. Also let you know how to engage S3 with EMR to process the apache log.


## Prerequisites
>The workshop’s region will be in ‘N.Virginia’

>Download both **access-log-20140105** and **do-reports2-edit.pig** two files.

## Lab tutorial
### Upload files to S3
1.1. 	In the **AWS Management Console**, on the **service** menu, click **S3**.

1.2. 	Click **Create bucket** button.

1.3. 	For bucket name, type **ecv-training-your-name**.

1.4.    Click **Create**.

1.5.    Click the bucket which you created, then click **Create folder** button, for folder name type **apache-log-analysis**, click **Save**.

1.6.    Click the **apache-log-analysis** folder which you created, click **Create folder** button to create second layer folders **log** and **output**.

1.7.    Click **Upload** to upload two file which you download from Github.

![1.png](/images/1.png)

### Launch an EMR cluster
2.1. 	In the **AWS Management Console**, on the **service** menu, click **EMR**.

2.2. 	Click **Create Cluster**.

2.3. 	Click **Go to advanced options**.

2.4 	In Step1: Software and Steps: for Release, choose **EMR 4.7.0**.

>It will automatically select Hadoop 2.7.2/Hive 1.0.0/Hue 3.7.1/Pig 0.14.0.

2.5. 	In the Add Step dialog, click **Auto-terminate cluster after the last step is completed**, select **Pig program** for step type.

![2.png](/images/2.png)

2.6 	Click **Configure**.
* For Script S3 location, type the location of the Pig script. For example:s3://elasticmapreduce/samples/pig-apache/do-reports2.pig.

* For Input S3 location, type the location of the input data. For example:s3://elasticmapreduce/samples/pig-apache/input.
* 
* For Output S3 location, type or browse to the name of your Amazon S3 output bucket.
* For Arguments, leave the field blank. 

* For Action on failure, select **Terminate cluster**.

* Click **Add**.

![3.png](/images/3.png)

2.8 	Click **Next** button.

2.9 	In Step2: Hardware Configuration:
* For Network: leave the default setting

* For Subnet: leave the default setting

* For Root device EBS volume size: leave the default setting
* In Node type dialog:
** For Master node, choose m3.xlarge as 1
    For Core node, choose m3.xlarge as 2
    For Task node, cancel the instance requirement

![4.png](/images/4.png)

2.10    Click **Next** button.

2.11    In Step3: General Cluster Setting:
