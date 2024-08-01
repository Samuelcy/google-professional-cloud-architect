Asynchronous Communication - Decoupled
- Create a topic and have your applications put log messages on the topic
- Logging service picks them up for processing when ready
- Advantages:
	- Decoupling: Publisher (Apps) don't care about who is listening
	- Availability: Publisher (Apps) up even if a subscriber (Logging Service) is down
	- Scalability: Scale consumer instances (Logging Service) under high load
	- Durability: Message is not lost even if subscriber (Logging Service) is down

Pub / Sub
- Reliable, scalable, fully-managed asynchronous messaging service
- Backbone for Highly Available and Highly Scalable solutions
	- Auto scale to process billions of messages per day
	- Low cost (Pay for use)
- Use cases: event ingestion and delivery for streaming analytics pipelines
- Supports push and pull message deliveries


Pub / Sub - How do they work?
- Publisher - Sender of a message
	- Publishers send messages by making HTTPS requests to pubsub.googleapis.com
- Subscriber - Receiver of the message
	- Pull - Subscriber pulls messages when ready 
		- Subscriber makes HTTPS requests to pubsub.google.apis.com
	- Push - Messages are sent to subscribers
		- Subscribers provide a web hook endpoint at the time of registration
		- When a message is received on the topic, A HTTPS POST request is sent to the web hook endpoints
- Very Flexible Publisher(s) and Subscriber(s) Relations: One to mkany, many to one, many to many

Pub / Sub - Getting ready with Topic and Subscriptions
- Step 1: Topic is created
- Step 2: Subscription(s) are created
	- Subscribers register to the topic
	- Each subscription represents discrete pull of messages from a topic:
		- Multiple clients pull same subscriptions => messages split between clients
		- Multiple clients create a subscription each => each client will get every message

Pub / Sub -Sending and receiving a message
- Publisher sends a message to Topic
- Message individually delivered to each and every subscription
	- Subscribers can receive message either by:
		- Push: Pub/ Sub sends the message to Subscriber
		- Pull: Subscribers poll for messages
- Subscribers send acknowledgement(s
- Message(s) are removed from subscriptions message queue
	- Pub / Sub ensures the message is retained per subscription until it is acknowledged

1. gcloud config set project glowing-furnace-304608
2. gcloud pubsub topics create topic-from-gcloud
3. gcloud pubsub subscriptions create subscription-gcloud-1 --topic=topic-from-gcloud
4. gcloud pubsub subscriptions create subscription-gcloud-2 --topic=topic-from-gcloud
5. gcloud pubsub subscriptions pull subscription-gcloud-2
6. gcloud pubsub subscriptions pull subscription-gcloud-1
7. gcloud pubsub topics publish topic-from-gcloud --message="My First Message"
8. gcloud pubsub topics publish topic-from-gcloud --message="My Second Message"
9. gcloud pubsub topics publish topic-from-gcloud --message="My Third Message"
10. gcloud pubsub subscriptions pull subscription-gcloud-1 --auto-ack
11. gcloud pubsub subscriptions pull subscription-gcloud-2 --auto-ack
12. gcloud pubsub topics list
13. gcloud pubsub topics delete topic-from-gcloud
14. gcloud pubsub topics list-subscriptions my-first-topic

Understanding Cloud Pub / Sub Best Practices
- Usecases:
	- Convert synchronous to asynchronous workflows
		- Also useful when consumer is unable to keep up with the producer (buffer data)
	- Apply transformations to IOT data stream
- Some use cases need in-order, exactly-once processing (de-duplication) for messages
	- Pub Sub supports in order processing:
		- Option --enable-message-ordering on subscription
	- Add Dataflow into to enable message deduplication (exactly- once processing)
		- Maintains a list of message Ids for a time period
		- If a message ID repeats, it is discarded (assumed to be a duplicate)

Cloud Dataflow
- Use pre-built tempaltes