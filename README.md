<p align="center">
    <img alt="SQS Mega" width=512 src="https://github.com/felipead/sqs-mega/raw/master/resources/logo/sqs-mega_blue_large.png">
</p>

---

SQS Mega is a minimal framework for robust messaging and async task processing based on [Amazon Simple Queue Service (SQS)](https://aws.amazon.com/sqs/). It has the following goals:

- Simplicity
- Resiliency
- Horizontal scalability
- Interoperability

It is ideal for event-driven **microservices** or other **distributed systems** that need to exchange data or process background tasks using the Producer-Consumer pattern. It leverages both the power and resiliency of Amazon SQS, packaged in a way that makes it simple to send or process messages using your platform of choice.

Although it is minimal and straightforward, it can replace intricated setups or heavy tools that could be difficult to learn, configure or scale, such as Celery, RabbitMQ, ActiveMQ, Sidekiq, Resque, delayed_job or even Kafta.

## Supported Platforms

- Python 3

The following platforms are planned:

- Rust
- Ruby
- Node.js
- JVM

## Amazon SQS

Amazon Simple Queue Service (SQS) is a fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications. SQS eliminates the complexity and overhead associated with managing and operating message oriented middleware, and empowers developers to focus on differentiating work. Using SQS, you can send, store, and receive messages between software components at any volume, without losing messages or requiring other services to be available.

SQS offers two types of message queues. Standard queues offer maximum throughput, best-effort ordering, and at-least-once delivery. SQS FIFO queues are designed to guarantee that messages are processed exactly once, in the exact order that they are sent.

Please read the [Amazon SQS Developer Guide](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html) to get started.

### Standard vs. FIFO Queues

Standard queue:

- _Unlimited Throughput_: Standard queues support a nearly unlimited number of transactions per second (TPS).
- _At-Least-Once Delivery_: A message is delivered at least once, but occasionally more than one copy of a message is delivered.
- _Best-Effort Ordering_: Occasionally, messages might be delivered in an order different from which they were sent.

![Standard Queue Diagram](https://github.com/felipead/sqs-mega/raw/master/resources/diagrams/sqs-what-is-sqs-standard-queue-diagram.png)

FIFO queue:

- _High Throughput_: By default, with batching, FIFO queues support up to 3,000 messages per second (TPS), per API action.
- _Exactly-Once Processing_: A message is delivered once and remains available until a consumer processes and deletes it. Duplicates aren't introduced into the queue.
- _First-In-First-Out Delivery_: The order in which messages are sent and received is strictly preserved.

![FIFO Queue Diagram](https://github.com/felipead/sqs-mega/raw/master/resources/diagrams/sqs-what-is-sqs-fifo-queue-diagram.png)

FIFO queues are more expensive to scale. For this reason, chose Standard queues unless your application explicitly requires exactly-once processing and preserving the order of messages. Most applications can live well without such requirements.

Design your application code to be **idempotent**. This way, even if you receive duplicate or out-of-order messages, the outcome remains the same.
