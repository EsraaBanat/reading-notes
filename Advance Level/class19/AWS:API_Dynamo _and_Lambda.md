# AWS: API, Dynamo and Lambda

## AWS API Gateway

### What is Amazon API Gateway?

**Amazon API Gateway** is a managed service that allows developers to define the HTTP endpoints of a REST API or a WebSocket API and connect those endpoints with the corresponding backend business logic. It also handles authentication, access control, monitoring, and tracing of API requests.

API Gateway integrates with many other AWS services like AWS Lambda, AWS SNS, AWS IAM, and Cognito Identity Pools. These integrations allow for fully managed authentication and authorization layers, as well as detailed metrics and tracing for API requests.

![](https://assets-global.website-files.com/60acbb950c4d66d0ab3e2007/614dc8866ca06e6d1740ca01_amazon-api-gateway-guide-1.png)

### Why is Amazon API Gateway an important part of the Serverless ecosystem?

Within the Serverless ecosystem, API Gateway is the piece that ties together Serverless functions and API definitions. Being able to trigger the execution of a Serverless function directly in response to an HTTP request is the key reason why API Gateway is so valuable in Serverless setups: it enables a truly serverless architecture for web applications. When using API Gateway together with other AWS services, it’s possible to build a fully functional customer-facing web application without maintaining a single server yourself.

### How does API Gateway integrate with other AWS services?

Many AWS services support integration with Amazon API Gateway, including:

- **AWS Lambda**: run Lambda functions to generate HTTP API responses.
- **AWS SNS**: publish SNS notifications when an HTTP API endpoint is accessed.
- **Amazon Cognito**: provide authentication and authorization for your HTTP APIs.

API Gateway supports direct integrations that can be configured in the API Gateway user interface (or via the API Gateway’s own API) for the following actions:

- Invoking an AWS Lambda function.
- Invoking another HTTP endpoint, with or without VPC Link.
- Making an HTTP call against the API of any AWS service that provides an HTTP API.
- Returning a mock response generated within API Gateway without calling out to other services.

![](https://assets-global.website-files.com/60acbb950c4d66d0ab3e2007/614dc95513b10738e2cf2eb8_amazon-api-gateway-guide-2.png)

### Benefits of Amazon API Gateway

- Map HTTP requests to specific functions in a Serverless application via an API Gateway event.

- Connecting HTTP endpoints to individual functions is straightforward with API Gateway, obviating the need for a dedicated API server

- Map WebSocket events to Serverless functions. If you are building a WebSocket API, API Gateway also lets you map its events to a Serverless function. This works great for real-time functionality like in-app updates and notifications.

- Use multiple microservices to serve the same top-level API. API Gateway makes it easy to have different Serverless functions serving different parts of your API. This means you can better encapsulate your functionality into each function and clearly separate the business logic of different parts of your API. Another benefit here is that you can transparently replace the function called by a given API request—the users won’t notice any change on the API layer.

- Save time with integrations: authentication, developer portal, CloudTrail, CloudWatch. API Gateway allows you to implement a fully managed authentication and authorization layer by using Amazon Cognito and Lambda custom authorizers without running your own auth systems. By using API Gateway you also get access to the developer portals that are generated automatically from your API schemas. In addition, CloudTrail, CloudWatch and X-RAY all integrate with API Gateway, simplifying the profiling and debugging of API requests

### Amazon API Gateway limits

- **Regional APIs**: you can only have 600 regional APIs per AWS account. That’s a lot; most teams won’t reach this limit.
- **Integration timeouts**: the shortest possible timeout for an integration in API Gateway is 50 ms, and the longest is 29 seconds.
- **Payload size**: the maximum payload size that can be returned by an API endpoint is 10MB. If you’re planning to return more data per request than that, you may need to split up the payload into multiple pages.

### How API Gateway Works


![](https://d1.awsstatic.com/serverless/New-API-GW-Diagram.c9fc9835d2a9aa00ef90d0ddc4c6402a2536de0d.png)

### API Types

**1. RESTful APIs:**
Build RESTful APIs optimized for serverless workloads and HTTP backends using HTTP APIs. HTTP APIs are the best choice for building APIs that only require API proxy functionality. If your APIs require API proxy functionality and API management features in a single solution, API Gateway also offers REST APIs.

**2. WEBSOCKET APIs**
Build real-time two-way communication applications, such as chat apps and streaming dashboards, with WebSocket APIs. API Gateway maintains a persistent connection to handle message transfer between your backend service and your clients.

## AWS DynamoDB Guide

**DynamoDB** is a hosted NoSQL database offered by Amazon Web Services (AWS)

DynamoDB is a particularly good fit for the following use cases

- Applications with large amounts of data and strict latency requirements.

- Serverless applications using AWS Lambda.

- Data sets with simple, known access patterns.

### How it works
Amazon DynamoDB is a fully managed, serverless, key-value NoSQL database designed to run high-performance applications at any scale. DynamoDB offers built-in security, continuous backups, automated multi-Region replication, in-memory caching, and data export tools.


![](https://d1.awsstatic.com/product-page-diagram_Amazon-DynamoDBa.1f8742c44147f1aed11719df4a14ccdb0b13d9a3.png)

## Dynamoose

**Dynamoose** is a modeling tool for Amazon's DynamoDB

### Key Features

- Type safety
- High level API

- Easy to use syntax

- Ability to transform data before saving or retrieving documents

- Strict data modeling (validation, required attributes, and more)
- Support for DynamoDB Transactions
- Powerful Conditional/Filtering Support
- Callback & Promise support

### Installation:

```
npm install --save dynamoose
```

### Import
In order to use Dynamoose you must import it or require it in your project. This will make the `dynamoose` namespace accessible so you can use things like models, schemas, and more.

```
const dynamoose = require("dynamoose");
```

# References

### [AWS API Gateway Overview](https://www.serverless.com/guides/amazon-api-gateway)

### [AWS API Gateway](https://aws.amazon.com/api-gateway/)

### [AWS DynamoDB Guide](https://www.dynamodbguide.com/what-is-dynamo-db/)

### [AWS DynamoDB](https://aws.amazon.com/dynamodb/)

### [Dynamoose](https://dynamoosejs.com/getting_started/Introduction/)

## [Back To Home Page](../../README.md)
