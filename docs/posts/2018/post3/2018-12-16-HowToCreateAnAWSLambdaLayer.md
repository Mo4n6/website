---
layout: post
title: How to Create an AWS Lambda Layer
date:   2018-12-16
description: Does writing a Lambda function takes too long?  Well... here is how you can save time by layering libraries, custom runtime, or other dependencies all the way down.

tags:
- AWS
- Lambda Layer
- Dev
- Python
- Twitter
share: true
toc: true
---

---

[![post][1]][1]

*AWS Lambda Layer*

---

## Introduction
This article will walk you through creating an AWS Lambda Layer.  

### What is a Lambda Layer?

A layer is a Zip file that contains libraries, a custom runtime, or other dependencies for your Lambda function.

## Instructions
The process to create a Lambda layer is broken down into the following steps:

1. Creating the .Zip Library
1. Creating a Lambda Layer
1. Adding a Layer to a Lambda Function

### Step 1 - Creating the .Zip Library
To create a library you need to create a ZIP file of the library.  You need to place the library in one of the folders that is supported by the runtime.

Link: [Lambda Layer Library Configurations](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html#configuration-layers-path)

For example for Python, you need to place the library in the specific python runtime folder:

---

[![post][2]][2]

*Python Layer Folder Structure*

---

The .ZIP file can be given any name.  For example if you're including the twitter library, you can name it 'twitter.zip'.  Here is how the .ZIP file may look:

---

[![post][3]][3]

*Twitter Layer Folder*

---

### Step 2 - Creating a Lambda Layer
Log in to AWS Management Console and go to the Lambda service.  Click on Layers on the left hand side and select Create Layer.

---

[![post][4]][4]

*AWS Lambda Layers*

---

---

[![post][5]][5]

*Create a Layer*

---

Fill out the Create Layer form, you will need to upload the .ZIP file created in Step 1 of this article.  You will need to provide a link of the license information for the library.

---

[![post][6]][6]

*Layer Created*

---

### Step 3 - Adding a Layer to a Lambda Function
Once you've created the Lambda Layer, you need to add it to a Lambda Function.  To do this, open up the Lambda Function.  Click on Layers and click on Add a Layer.

---

[![post][7]][7]

*A Lambda Function*

---

Select your layer and version of the layer.  You can also provide a layer version ARN to select a public layer.

---

[![post][8]][8]

*Add layer to Function*

---

Now that you added the layer to your function, it should be listed under 'Referenced layers'.

## Summary

This article introduced layers, showed how you can create a layer and reference it in a Lambda Function.  These layers can be used for various Lambda functions.  There is a concept of Merge order and Public Layers that I didn't touch on in this article.  We will explore these options in future articles.


[1]: ./../../../assets/images/2018-12-16-HowToCreateAnAWSLambdaLayer/P3-Image01.PNG
[2]: ./../../../assets/images/2018-12-16-HowToCreateAnAWSLambdaLayer/P3-Image03.PNG
[3]: ./../../../assets/images/2018-12-16-HowToCreateAnAWSLambdaLayer/P3-Image05.PNG
[4]: ./../../../assets/images/2018-12-16-HowToCreateAnAWSLambdaLayer/P3-Image02.PNG
[5]: ./../../../assets/images/2018-12-16-HowToCreateAnAWSLambdaLayer/P3-Image04.PNG
[6]: ./../../../assets/images/2018-12-16-HowToCreateAnAWSLambdaLayer/P3-Image06.PNG
[7]: ./../../../assets/images/2018-12-16-HowToCreateAnAWSLambdaLayer/P3-Image07.PNG
[8]: ./../../../assets/images/2018-12-16-HowToCreateAnAWSLambdaLayer/P3-Image08.PNG
