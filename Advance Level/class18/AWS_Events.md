# AWS: Events

## Difference between SQS and SNS

SQS and SNS are important components for scalable, large scale, distributed, cloud-based applications:

### **1. SNS**

 SNS — **S**imple **Q**ueue **S**ervice --> a distributed **publish-subscribe** service

 ![](https://miro.medium.com/max/622/1*mdUPKzrfJFuXa4d43KhKUQ.png)

 Amazon SNS is a fast, flexible, fully managed push notification service that lets you send individual messages or to bulk messages to large numbers of recipients. Amazon SNS makes it simple and cost effective to send push notifications to mobile device users, email recipients or even send messages to other distributed services.

SNS is a distributed publish-subscribe system. Messages are pushed to subscribers as and when they are sent by publishers to SNS.

SNS supports several end points such as email, sms, http end point and SQS. If you want unknown number and type of subscribers to receive messages, you need SNS.

With Amazon SNS, you can send push notifications to Apple, Google, Fire OS, and Windows devices , as well as to Android devices in China with Baidu Cloud Push. You can use SNS to send SMS messages to mobile device users in the US or to email recipients worldwide.

### **2. SQS**

 SQS — **S**imple **N**otification **S**ervice --> distributed **queuing** service

 ![](https://miro.medium.com/max/868/1*7eL3udb6Cto4I9Ly1sN8oA.jpeg)

 Amazon SQS is a fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications.

SQS is distributed queuing system. Messages are not pushed to receivers. Receivers have to poll SQS to receive messages. Messages can be stored in SQS for short duration of time (max 14 days).

Messages can’t be received by multiple receivers at the same time. Any one receiver can receive a message, process and delete it. Other receivers do not receive the same message later. Polling inherently introduces some latency in message delivery in SQS unlike SNS where messages are immediately pushed to subscribers.


| **Key Differences** | **SQS**                                                                                                                                          | **SNS**                                                                                                                                                                      |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Entity Type**         | Queue (similar to JMS, MSMQ).                                                                                                                    | Topic-Subscriber (Pub/Sub system)                                                                                                                                            |
| **Message consumption** | Pull Mechanism — Consumers poll messages from SQS                                                                                                | Push Mechanism — SNS pushes messages to consumers                                                                                                                            |
| **Persistence**         | Messages are persisted for some duration is no consumer available. The retention period value is from 1 minute to 14 days. The default is 4 days | No persistence. Whichever consumer is present at the time of message arrival, get the message and the message is deleted. If no consumers available then the message is lost |
| **Consumer Type**       | All the consumers are supposed to be identical and hence process the messages in exact same way                                                  | All the consumers are (supposed to be) processing the messages in different ways                                                                                             |


## Use Cases

### Choose SNS if:

- You would like to be able to publish and consume batches of messages.
- You would like to allow same message to be processed in multiple ways.
- Multiple subscribers are needed.

### Choose SQS if:

- You need a simple queue with no particular additional requirements.
- Decoupling two applications and allowing parallel asynchronous processing.
- Only one subscriber is needed.

> We can design fanout pattern by using both SNS and SQS. In this pattern, a message published to an SNS topic is distributed to multiple SQS queues in parallel.




# References

### [AWS SQS vs SNS](https://medium.com/awesome-cloud/aws-difference-between-sqs-and-sns-61a397bf76c5)

### [AWS SNS and SQS](https://www.youtube.com/watch?v=mXk0MNjlO7A)

### [SQS and SNS Basics](https://www.youtube.com/watch?v=UesxWuZMZqI)

## [Back To Home Page](../../README.md)
