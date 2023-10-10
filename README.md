# Introduction
In the ever-evolving landscape of API development, dealing with legacy systems and formats is a common challenge. This blog post aims to assist you in leveraging AWS API Gateway and AWS Lambda to address a specific scenario: transforming XML data to JSON and vice versa. We'll delve into the techniques supported by AWS API Gateway and AWS Lambda that allow you to bridge the gap between these formats seamlessly.
# Understanding the Challenge:
Legacy systems often communicate using XML, while modern APIs tend to rely on JSON due to its simplicity and widespread support. In scenarios where your API needs to interact with both formats, a transformation mechanism becomes crucial. AWS API Gateway and Lambda can be the solution to ensure a smooth transition between XML and JSON. This scenario can occur even with your own system. Imagine that you have a legacy application that uses XML standards for integration. To modernize your application, you can explore the option to migrate your backend to JSON standards first and explore the power of AWS API Gateway and Lambda to transform your data between frontend and backend. This will give you the ability to modernize your app in chunks.
# Lab Scenario
In this lab scenario, we will do following tasks:
1. Deploy a simple java application that expose SOAP APIs by using AWS Elastic Beantalk
2. Deploy a simple Nodejs AWS Lambda function that  transforms JSON request into a SOAP message and interacts with the SOAP service. A reverse path is followed during the response flow.
3. Deploy AWS API Gateway which will forward request to AWS Lambda
4. Test REST APIs
<img width="581" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/08da1bba-bebd-48c4-8bce-69509bd978d8">

# 1. Deploy a simple java application that expose SOAP XML APIs by using AWS Elastic Beantalk
1. Open AWS [Elastic Beantalk](https://ap-southeast-1.console.aws.amazon.com/elasticbeanstalk/home?region=ap-southeast-1#/welcome)
<img width="950" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/36d61276-496b-4f98-8b69-3712aa02a516">

2. Create AWS Elastic Beantalk (by clicking on Create Application)
<img width="879" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/e4ab25eb-88e8-4412-b802-f681e397a579">
<img width="876" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/8d4e35d0-d97b-4e69-8bf0-b9fc263faf16">
<img width="890" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/54ed95e7-1ed4-476a-b037-64a1c5870e62">

Upload .jar file from your local device [Jar file] (https://github.com/binhtq80/aws-labs/blob/main/gs-producing-web-service-0.1.0.jar)
<img width="886" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/3ebcff91-12e2-4f8d-a049-10cd4f18de7d">



<img width="886" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/b7ebc4c9-799a-42f8-830c-60c151016efa">








3. 
4. 
5. 
