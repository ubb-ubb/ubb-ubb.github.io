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

# Queues, Topics, Exchanges

# MQ Comparison

