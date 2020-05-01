<p align="center">
    <img alt="SQS Mega" width=500 src="https://github.com/felipead/sqs-mega/raw/master/resources/logo/sqs-mega_blue_large.png">
</p>

---

SQS Mega is a minimal framework for robust messaging and async task processing based on [Amazon Simple Queue Service (SQS)](https://aws.amazon.com/sqs/). It has the following goals:

- Simplicity
- Resiliency
- Horizontal scalability
- Interoperability

It is ideal for event-driven **microservices** or other **distributed systems** that need to exchange data or process background tasks using the Producer-Consumer pattern. It leverages both the power and resiliency of Amazon SQS, packaged in a way that makes it simple to send or process messages using your platform of choice.

Although it is minimal and straightforward, it can accomplish what usually requires heavy tools that could be difficult to learn or configure, such as Celery, RabbitMQ, ActiveMQ, Sidekiq, Resque, or even Kafta.

## Supported Platforms

- Python 3

The following platforms are planned:

- Rust
- Ruby
- Node.js
- JVM
