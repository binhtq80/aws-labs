# Introduction
In the ever-evolving landscape of API development, dealing with legacy systems and formats is a common challenge. This blog post aims to assist you in leveraging AWS API Gateway and AWS Lambda to address a specific scenario: transforming XML data to JSON and vice versa. We'll delve into the techniques supported by AWS API Gateway and AWS Lambda that allow you to bridge the gap between these formats seamlessly.
# Understanding the Challenge:
Legacy systems often communicate using XML, while modern APIs tend to rely on JSON due to its simplicity and widespread support. In scenarios where your API needs to interact with both formats, a transformation mechanism becomes crucial. AWS API Gateway and Lambda can be the solution to ensure a smooth transition between XML and JSON. This scenario can occur even with your own system. Imagine that you have a legacy application that uses XML standards for integration. To modernize your application, you can explore the option to migrate your backend to JSON standards first and explore the power of AWS API Gateway and Lambda to transform your data between frontend and backend. This will give you the ability to modernize your app in chunks.
# Lab Scenario
In this lab scenario, we will do following tasks:
1. Deploy a simple java application that expose SOAP APIs by using AWS Elastic Beantalk
2. Deploy a simple Nodejs AWS Lambda function that  transforms JSON request into a SOAP message and interacts with the SOAP service. A reverse path is followed during the response flow.
3. Deploy AWS API Gateway
