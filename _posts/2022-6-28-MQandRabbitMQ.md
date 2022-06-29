---
layout: post
title: Rabbit MQ
published: true
---

# Why we use messaging systems?

- Form of communication
- Provides loosely-coupling
- Exchange information
- Typical software message has header and body
  
Example: E-commerce site on black friday

Might crash because of the load!! Processing all the request is impossible. Instead of processing all at once, we need to queue these transactions. Otherwise it will be hard to handle.

Advanced Messaging Protocols has come to rescue! Threse protocols provide, 
- Actual type of message,
- Advanced structures for messages to flow through;
  - Queues
  - Topics
  - Channels
  - Exchanges and more...  

# Messaging Protocols

Three of them widely used. 

- AMQP: Advanced message queueing protocol. Reliable and interoperable. Highly standardized. Provides queueing topic based publish-subscribe, flexible routing etc.
- STOMP: Simple text-oriented messaging protocol.
Very simple and easy to implement.
Does not deal with queues and topics.
Uses SEND semantic with destination. Consumers of messages Subscribe to these destinations. 
- MQTT: Message Queue Telemetry Transport.
Machine to machine. Highly standardized. Simply publish-subscribe messaging. Designed for resource constrained devices and low bandwidth. Ideal for mobile and IoT. Supports thousands concurrent device connections.

# What is AMQP?

Provides exchange communication and messaging between two different computer systems. Diverse programming languages can communicate easily. Advanced publish-and-subscribe. Transactional messaging functionality.

Uses:
- Real time feed of constantly updating information.
- Encrypted assured transaction
- Message to be delivered when destionation is online.
- Send enourmous message while still receiving status updates.
- Work on all popular operating systems and langugages.


# RabbitMQ

Open source message broker. Most popular implementation of AMQP. 

!["Design schema"](https://i.ibb.co/4WNZ9PJ/rabbitmq.png)

# Exchanges, Queues, Topics, Bindings

!["4 Actors"](https://i.ibb.co/n7h09Bg/actors.png)

## Exchanges

- Messages sent first to Exchange.
- Takes a message and routes it to **one or more** Queue.
- Routing algorithm decides where to send messages from exchange
- Routing algorithms depends on the exchange type and rules called bindings. 

4 Exchange Types:
- Direct Exchange: Empty string or amq.direct direction for any exchange. Default exchange when you say no binding. amq.direct 
- Fanout Exchange: Fanout used as message distribution for everywhere. All the bindings message has. amq.fanout 
- Topic Exchange: Choosing topic to send, define a topic send your message using that topic. amq.topic
- Headers Exchange: Way to exchange with headers. amq.match  

## Queues

- Core element.
- Messages are routed from exchange to queues with bindings.
- Queues are final destination before received from Subscriber.
- Routing algorithms depends on exchange type and rules called bindings.
- Bindings bind exchanges to queues for message delivery.
- Name: Name of queue
- Durable: Persist queue to disk or not?
- Exclusive: Delete queue if not used anymore.
- Auto-delete: Delete queue if consumer unsubscribes.

## Topics

- Subject part of the message.
- Defined as routing_key for message grouping.
- Optional parameters for message exchange
  
## Bindings

- Rules that exchanges use to route messages to queues.
- Routing key acts like a filter.
- If message can not be routed to any queue, either dropped or returned to publisher.
