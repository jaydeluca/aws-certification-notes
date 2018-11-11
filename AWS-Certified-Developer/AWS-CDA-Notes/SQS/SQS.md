# SQS - Simple Queue Service
## What is SQS?
Amazon SQS is a web service that gives you access to a maessage queue that can be used to store messages while waiting for a computer to process them.

Amazon SQS is a distributed queue system that enables web service applications to quickly and reliably queue messages that one component in the application generates to be consumed by another component. A queue is a temporary repository for messages that are awaiting processing.

- Oldest AWS Service
- A way of assigning jobs



## Meme Website Example

![Image](https://i.imgur.com/heG8oQl.jpg?1)


The queue acts as a buffer betweeen the component producing and saving data, and the component receiving the data for processing. This means the queue resolves issues that arise if the producer is producing work faster than the consumer can process it, or if the producer or consumer are only intermittently connected to the network


## Queue Types
There are two types of Queue:
- Standard Queues (default)
- FIFO Queues (First-In-First-Out)

## Standard Queues
Amazon SQS offers standard as the default queue type. A standard queue lets you have a nearly-unlimited number of transactions per second. Standard queues guarantee that a message is delivered at least once. However, occasionally (because of the highly-distributed architecture that allows high throughput), more than one copy of a message might be delivered out of order. Standard queues provide best-effort ordering which ensures that messages are generally delivered in the same order as they are sent. 

## FIFI Queues
The FIFO queue complements the standard queue. The most important features of this queue type are FIFO (First-In-First-Out) delivery and exactly-once processing: The order in which messages are sent and received is strictly preserved and a message is delivered once and remains available until a consumer processes and deletes it: duplicates are not introduced into the queue. FIFO queues are also support message groups that allow multiple ordered message groups within a single queue. FIFO queues are limited to 300 transactions per second (TPS), but have all the capabilities of standard queues.

## SQS key Facts
- SQS is a pull-based system, not push-based
- Messages are 256 KB in size
- Messages can be kept in the queue from 1 minute to 14 days
- Default retention period is 4 days
- SQS guarantees that your message will be processed at least once.

## SQS Visibility Timeout
- The Visibility Timeout is the amount of time that the message is invisible in the SQS queue after a reader picks up that message. Provided the job is processed before the visibility time out expires, the message will then be deleted from the queue. Ifthe job is not processed within that time, the message will become visible again and another reader will process it. This could result in the same message being delivered twice.
- Default Visibility Timeout is 30 seconds
- Increase it if your task takes > 30 seconds
- Maximum is 12 hours

## SQS Long Polling 
- Amazon SQS long polling is a way to retrieve messages from your Amazon SQS queues
- While the regular short polling returns immediately (even if the message queue being polled is empty), long polling doesn't return a response until a message arrives in the message queue, or the long poll times out
- As such, long polling can save you money

## SQS - Exam Tips
 - SQS is a distributed message queueing system
 - Allows you to decouple the components of an application so that they are independent
 - **Pull-based**, not push-based
- Standard Queues (default) - best-effort ordering; message delivered at least once
- FIFO Queues (First In First Out) - ordering is strictly preserved, message delivered once, no duplicates.
    - e.g. good for banking transactions which need to happen in strict order
- Visibility Timeout
    - Default is 30 seconds - increase if your task takes > 30 seconds to complete
    - Max 12 hours
- Short Polling - returned immediately even if no messages are in the queue
- Long Polling - polls the queue periodically and only returns a response when a message is in the queue or the timeout is reached







