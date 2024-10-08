- Check [[Apache Kafka vs RabbitMQ]] for more  detailed comparisons.
- A [[message broker]] is designed to store and transmit messages between distributed components, ensuring that no data is lost in the process, while [[stream]]ing focuses on real-time data processing and analytics.
- Message brokers are suitable for scenarios where the primary concern is reliability, as they offer guaranteed delivery, message persistence, and consumer acknowledgments.
- Streaming excels in situations where real-time analysis and processing of data are crucial, as it offers low-latency data transfer and allows for data analysis across multiple time windows.
- Once messages are written to a stream, they stay there. Conversely, with a message broker, a message is removed from the [[message queue]] and then passed to a service's consumer.
	- [[RabbitMQ]] removes the messages where as [[Apache Kafka]] retains them
	- NOTE that a message is only removed when it has been successfully consumed.
- Both Streams and Message Brokers often work together particularly in large scale systems.