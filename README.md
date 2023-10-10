<img width="890" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/7835cf80-bdab-4a23-b27d-604ef62e3d76"># Introduction
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

Step1: Configure environment
<img width="879" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/e4ab25eb-88e8-4412-b802-f681e397a579">
<img width="876" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/8d4e35d0-d97b-4e69-8bf0-b9fc263faf16">
<img width="890" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/54ed95e7-1ed4-476a-b037-64a1c5870e62">

Upload .jar file from your local device [Jar file] (https://github.com/binhtq80/aws-labs/blob/main/gs-producing-web-service-0.1.0.jar)
<img width="886" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/3ebcff91-12e2-4f8d-a049-10cd4f18de7d">
<img width="886" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/b7ebc4c9-799a-42f8-830c-60c151016efa">

Step2: Configure service access
<img width="906" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/3e86ff80-eccf-4d5e-9e8e-91aba1f269ad">
Step3: Setup networking (we dont need need database in this lab)
<img width="946" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/7142f978-45a8-40ab-a97e-fd46d655c3e4">
Leave Database and Tags as default
<img width="902" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/41f7a028-8e5b-4efd-af7e-ceb3429c38f2">

<img width="892" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/d055f055-654b-4260-9182-631d325a568c">

Step4: Configure instance traffic and scaling
Select EC2 security groups and leave other section as default
<img width="910" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/15f797b8-fa33-4b82-9551-9bab99666799">

Step5: Configure updates, monitoring, and logging
Select Enhanced Health Reporting and leave the rest as default
<img width="894" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/8ffeb51f-1f07-4425-8b35-88eb20c2377d">

Add SERVER_PORT environment variable

<img width="901" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/6d66fbc6-ffd8-4655-9bb0-1e267d6006fb">

Step6: Review and Submit
<img width="880" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/0f090936-c1a0-4540-943a-13c1c0d8aaea">

Step7: Wait for Elastic BeanTalk environment deployment successs

<img width="881" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/100e4410-0f4c-48ab-91a2-f7e2a6575ede">

Step8: Test if we can access the service description language (which is use to build client)

<img width="948" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/7091a00c-9d9f-4b48-a684-2e51432c525c">

# 2. Next, we will develop and deploy a simple Nodejs AWS Lambda function that  transforms JSON request into a SOAP message and interacts with the SOAP service. A reverse path is followed during the response flow.

1. Open [AWS Lamda] (https://ap-southeast-1.console.aws.amazon.com/lambda/home?region=ap-southeast-1#/functions)
2. Create AWS Lamda function (click on Create Function)
<img width="892" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/bdc87e4b-8bd0-4295-be9b-af914c3ed6d6">
<img width="891" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/62cc959f-6661-4f9e-bfe9-47c17067313c">

Clink on Advanced Setings and configure VPC where we're hosting our SOAP web service so that our Lambda function cac access it as in the samme local network (VPC)
<img width="917" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/648152e4-b4bc-461c-b66f-25a12589beed">

Select security group and click create function
<img width="891" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/19da2b92-4da4-4d4f-a7f8-d879fb473bc2">

3. Upload Notejs code to AWS Lambda function
Click on the function just created and select **Upload from**
<img width="899" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/315da0b6-26b9-4fa3-a77b-40a9b6234c1d">

Upload .zip file from your local device
<img width="944" alt="image" src="https://github.com/binhtq80/aws-labs/assets/31812579/ff7fe5a9-11cf-4faf-9cd9-3866aa61b3fb">




5. 





3. 















4. 
5. 
6. 
