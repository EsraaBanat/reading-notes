# AWS: S3 and Lambda

## **AWS S3**

**Amazon Simple Storage Service (Amazon S3)** is an object storage service offering industry-leading scalability, data availability, security, and performance. Customers of all sizes and industries can store and protect any amount of data for virtually any use case, such as data lakes, cloud-native applications, and mobile apps. With cost-effective storage classes and easy-to-use management features, you can optimize costs, organize data, and configure fine-tuned access controls to meet specific business, organizational, and compliance requirements.

![](https://d1.awsstatic.com/s3-pdp-redesign/product-page-diagram_Amazon-S3_HIW.cf4c2bd7aa02f1fe77be8aa120393993e08ac86d.png)

## Use cases:

1. Build a data lake
2. Back up and restore critical data
3. Archive data at the lowest cost
4. Run cloud-native applications

### To get the most out of Amazon S3, you need to understand a few simple concepts. Amazon S3 stores data as objects within buckets. An object consists of a file and optionally any metadata that describes that file. To store an object in Amazon S3, you upload the file you want to store to a bucket. When you upload a file, you can set permissions on the object and any metadata.

### Buckets are the containers for objects. You can have one or more buckets. For each bucket, you can control access to it (who can create, delete, and list objects in the bucket), view access logs for it and its objects, and choose the geographical region where Amazon S3 will store the bucket and its contents.

## **AWS Lambda Basics**

### What is AWS Lambda?

**AWS Lambda** is a serverless computing service provided by Amazon Web Services (AWS). Users of AWS Lambda create functions, self-contained applications written in one of the supported languages and runtimes, and upload them to AWS Lambda, which executes those functions in an efficient and flexible manner.

The Lambda functions can perform any kind of computing task, from serving web pages and processing streams of data to calling APIs and integrating with other AWS services.

### **Concept of Serverless :**

The concept of “serverless” computing refers to not needing to maintain your own servers to run these functions. AWS Lambda is a fully managed service that takes care of all the infrastructure for you. And so “serverless” doesn’t mean that there are no servers involved: it just means that the servers, the operating systems, the network layer and the rest of the infrastructure have already been taken care of, so that you can focus on writing application code.

### How does AWS Lambda work?

Each Lambda function runs in its own container. When a function is created, Lambda packages it into a new container and then executes that container on a multi-tenant cluster of machines managed by AWS. Before the functions start running, each function’s container is allocated its necessary RAM and CPU capacity. Once the functions finish running, the RAM allocated at the beginning is multiplied by the amount of time the function spent running. The customers then get charged based on the allocated memory and the amount of run time the function took to complete.

 **AWS Lambda a good fit for deploying highly scalable cloud computing solutions.**

### Use cases for AWS Lambdas :

1. individual tasks run for a short time
2. each task is generally self-contained
3. there is a large difference between the lowest and highest levels in the workload of the application.
4. Scalable APIs


### Benefits of using AWS Lambda

**1. Pay per use :** In AWS Lambda, you pay only for the compute your functions use, plus any network traffic generated. For workloads that scale significantly according to time of day, this type of billing is generally more cost-effective.

**2. Fully managed infrastructure :** Now that your functions run on the managed AWS infrastructure, you don’t need to think about the underlying servers—AWS takes care of this for you. This can result in significant savings on operational tasks such as upgrading the operating system or managing the network layer.

**3. Automatic scaling :** AWS Lambda creates the instances of your function as they are requested. There is no pre-scaled pool, no scale levels to worry about, no settings to tune—and at the same time your functions are available whenever the load increases or decreases. You only pay for each function’s run time.


**4. Tight integration with other AWS products :** AWS Lambda integrates with services like DynamoDB, S3 and API Gateway, allowing you to build functionally complete applications within your Lambda functions.

### Limitations of AWS Lambda

- Cold start time
- Function limits
- Not always cost-effective
- Limited number of supported runtimes

### **Getting started with AWS Lambda**

#### Creating AWS Lambda functions using the AWS console:

If you wish, you can use the AWS Lambda console to create your first function. In the AWS console, choose Lambda:

![](https://assets-global.website-files.com/60acbb950c4d6606963e1fed/612494806458a3049f598360_image%2081.png)

Once in the Lambda management console, click Create Function:

![](https://assets-global.website-files.com/60acbb950c4d6606963e1fed/61249480fbc97926a04d56a7_image%2080.png)

Add a name for your new function and choose the desired runtime. After that, click “Create function” to confirm the settings:

![](https://assets-global.website-files.com/60acbb950c4d6606963e1fed/61249511084c073ea39bb7ba_image%2082.png)

That’s it: the function is created, and you can now work on the function code and deploy the function directly in the Lambda console.

![](https://assets-global.website-files.com/60acbb950c4d6606963e1fed/612494809482ad5f5b35552f_image%2083.png)

We don’t recommend creating production Lambda functions via the management console for a two reasons:

Your function code will be limited to 30MB.
You’ll need to use the AWS web IDE to write the code in the browser. This IDE only provides very basic revision tracking and limits the collaboration on the code.



#### Creating AWS Lambda functions using the Serverless Framework:

We recommend getting started with AWS Lambda by using Serverless Framework. With the Serverless Framework, you can create Lambda functions using the tools you’re familiar with on your local machine and deploy to AWS in seconds. With this approach, your function’s code and configuration are located in the same Git repository which makes collaboration, change tracking and deployment of Lambda functions easier.
1. Install Serverless Framework on your machine:

    ‍
    `$ npm install serverless -g`

    ‍
2. Create a new service:

    ‍
    `$ serverless`

    ‍
3. Add the resources your function needs to the serverless.yml file. Check out the AWS Intro doc for an example of this file and the list of options you can configure there.
    ‍
4. Add code to your service. See the Serverless AWS provider docs for specific steps you can follow to create your functions.
    ‍
5. Deploy to AWS by running the deploy step:

    ‍
    `$ serverless deploy`


That’s it! Your function will be deployed and you’ll see the URL of the function’s endpoint in your console.

## Content Delivery Network (CDN)

 **Content Delivery Network (CDN)** is a geographically distributed group of servers that work together to provide fast delivery of Internet content. A CDN allows for the fast transfer of data needed for loading Internet content including HTML pages, javascript files, stylesheets, images, and videos.

![](https://cyberhoot.com/wp-content/uploads/2020/03/What-is-Content-Delivery-Network-1024x647.jpg)

CDNs work through servers nearest to the website visitor respond to the request. The content delivery network copies the pages of a website to a network of servers that are spread out at geographically different locations, caching the contents of the page. When a user requests a webpage that is part of a content delivery network, the CDN will redirect the request from the originating site’s server to a server in the CDN that is closest to the user and deliver the cached content. CDNs will also communicate with the originating server to deliver any content that has not been previously cached. In turn, the speed is improved by distributing content closer to the website visitors by using a nearby CDN server, causing visitors to experience faster page loading times. In simpler terms, for example, instead of a user in London trying to access a server in LA, which can cause slower Internet speeds, the user would be redirected through a CDN that is geographically closest to them (London, Paris, Stockholm, etc). As of today, the majority of web traffic goes through through CDNs, including traffic from major sites like Facebook, Netflix, and Amazon.

Employing a CDN doesn’t only speed up the delivery of Internet content, it helps protect your website against certain forms of cyber attacks, such as Denial of Service attacks. It protects against these threats because CDNs allow for the handling of more traffic and withstanding hardware failure better than many origin servers.

# References

### [AWS S3](https://aws.amazon.com/s3/)

### [AWS Lambda Basics](https://www.serverless.com/aws-lambda)

### [CDN](https://cyberhoot.com/cybrary/content-delivery-network-cdn/)

## [Back To Home Page](../../README.md)
