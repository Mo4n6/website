---
layout: post
title: How to Create an AWS Lambda Function
date:   2018-11-12
description: What's cooler than a Twitter App that runs on your laptop and sends tweets?  A Twitter App that runs in the cloud and tweets based on a pre-defined schedule.  This article will not only save you money on your electricity bill, it will walk you through how to create a Lambda function.
tags:
- AWS
- Lambda
- Dev
- Python
share: true
toc: true
---

---

[![post][1]][1]

*AWS Lambda*

---

## Introduction

This article will walk you through how to create an AWS Lambda Function.  An AWS Lambda Function consists of a Trigger, Function and Resources.The Trigger will be generated based on an event.  An example of an event that is a 'CloudWatch Event'.  The 'CloudWatch Event' can be configured to generate a trigger based on a specified schedule.  The Function will be executed once an event is triggered.  We will go into more details later.

---

[![post][2]][2]

*Designer Window*

---

The function can be written in  different programming languages.  Here is a list of these languages:

---

[![post][3]][3]

*AWS Lambda Runtime Frameworks*

---

## Instructions
The process to create a Lambda Function is broken down into the following steps:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 1 - AWS Account Overview  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 2 - Create a Lambda Function  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 3 - Add Trigger from 'CloudWatch Event'
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 4 - Create the Handler Function
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 5 - Zip your Code and Upload it
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 6 - Configure Test Event and Test

### Step 1 -  AWS Account Overview

You will need to sign up for an AWS Account.  The sign up process will require you to enter Credit Card information.  There are different tiers for an AWS account.  With the 'Free Tier' you can run 1M Requests per Month and 400,000 GB-seconds of compute time per month.

Links:
[Console AWS](https://console.aws.amazon.com/)
[AWS Lambda Pricing](https://aws.amazon.com/lambda/pricing/)


### Step 2 - Create a Lambda Function

Now that you've signed up for an AWS account, you're ready to create a Lambda function.

From 'Services' Menu select 'Lambda'.

---

[![post][4]][4]

*AWS Services*

---

Click on ' Create a function'.  Select 'Author from scratch'.

---

[![post][5]][5]

*Create a Function 1*

---

Fill in the 'Name' of the function, Runtime, Role and Role Name.

---

[![post][6]][6]

*Create a Function 2*

---

Roles are created based on the permissions that you want to grant to your AWS Lambda function.

AWS Lambda Permissions Model can be reviewed at https://docs.aws.amazon.com/lambda/latest/dg/intro-permission-model.html#lambda-intro-execution-role

### Step 3 - Add Trigger from 'CloudWatch Event'

Once you created your function, you will see something like this.  Click on 'CloudWatch Events' on the left tool bar.

---

[![post][7]][7]

*Create a Function 2*

---

Configure the trigger by configuring a new Rule.  You can use cron or rate expressions to configure the rule.  Here the rule is configured with cron (0 13 * * ? *) to run daily at 13:00 GMT.

Link for additional details on Cron Expressions:
[Cron Expressions](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/ScheduledEvents.html#CronExpressions)

---

[![post][8]][8]

*Creating a Trigger*

---

Save your function after configuring the Trigger Rule.  You will see something like this:

---

[![post][9]][9]

*Cron Expression Trigger*

---


### Step 4 - Create the Handler Function

Your code needs to contain a lambda event handler.  The name of the event handler function needs to be configured in the AWS Web GUI.  This is shown below:

---

[![post][10]][10]

*Lambda Handler Function*

---

The code for the event handler looks something like this:

``` python
import json
def lambda_handler(event, context):

# TODO implement
return {
  'statusCode': 200,
  'body': json.dumps('Hello from Lambda!')
}
```

Your code will need to include a handler similar to above.  The #ToDo implement can be replaced with main(), if you have a main() function defined in your code.

### Step 5 - Zip your Code and Upload it

Now that your code is ready.  There is one more step prior to creating a zip file.

Any 3rd party libraries that your code imports needs to be included in the .zip file.

For example, if your code imports Python-twitter libraries, you will need to install the libraries in the code directory.  This can be done with the following command executed from your code directory:

Windows:
```
pip install python-twitter -t .
```

Linux:
```
pip instaall python-twitter -t $(pwd)
```

After the code directory includes all the 3rd party libraries and the code, you need to create a .zip file that includes everything.  The .zip file may look something like this.

---

[![post][11]][11]

*Lambda Function .zip File*

---

Now upload the .zip file to the Lambda function.

---

[![post][12]][12]

*Upload .zip File*

---

### Step 6 - Configure Test Event and Test
Now you have created a trigger and uploaded your code, you're ready for testing.

Click on 'Test' button to create a test event.

---

[![post][13]][13]

*Test*

---

Here is how the test event creation may look like:

---

[![post][14]][14]

*Create Test Event*

---

You can configure the test event based on the scenario you want to test.  If your code doesn't require any input parameters, you can click on 'Create' to test your code.  Make sure to 'Save' your function periodically.

## Summary
You're done!!! Good Job, you've created a lambda function.  Here are some things that you might of done if you followed through with the article:

* Setup and configured your 'free tier' AWS account.
* Created an AWS Lambda Function.
* Added a 'CloudWatch Event' to trigger your function once a day.
* Added an event handler function to your code to handle the trigger from the 'CloudWatch Event'.
* Installed 3rd party libraries in your code directory.
* Created a .zip archive for your code and uploaded it.
* Created a Test event to test out your code.

In a future article I'll touch base on how to do this with AWS SAM (Serverless Application Model) CLI.


[1]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image1.png
[2]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image3.png
[3]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image2-2.png
[4]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image4.png
[5]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image5.png
[6]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image6.png
[7]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image7.png
[8]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image8.png
[9]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image9.png
[10]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image10.png
[11]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image11.png
[12]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image12.png
[13]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image13.png
[14]: ./../../../assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image14.png
