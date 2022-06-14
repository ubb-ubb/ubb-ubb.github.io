---
layout: post
title: Software Patterns
published: true
---

___Read Software Architecture Patterns by Mark Richards___  
___Add visuals___

Design patterns shows characteristics of the project. It's organization of a system. It includes all components, how they interact with eachother, environment they operate and principles used to design the software.

## Layered Architecture

Layers are isolated from each other. It provides seperation of concerns.

Closed Layer: If bottom layer is wanted to be reachable from upper side of the layers, its not possible to bypass closed layer, between upper and bottom layer.
Open Layer: You can bypass open layer to reach below layer.  

Sample layers:  
Presentation Layer  
Business Layer  
Persistance Layer  
Database Layer  

Sinkhole, meaning processes in layers is not fruitful.  

Testability is great. Since all aspects are seperated.

Not-Easy to Deploy.  

## Client Server Architecture  

Client Server Architecture is a computing model in which the server hosts, delivers and manages most of the resources and services to be consumed by the client.

## Master Slave Architecture  

In computer science, the master/slave architecture initially started in the context of database replication.
For example, if theres a database where data is replicated across 3 servers. There are chances that atleast one of these could be out of sync with others. In such cases how to resolve the inconsistency? With the master-slave architecture, one replica is identified as the master and the others serve as slaves. The new terminology is primary vs replica (or secondary).

In the case of database, typically, the clients will read and write to the master (some times reads are done on slaves too), and the data are copied asynchronously to the slaves.
The slaves are typically used when the master fails or for batch processing if the client(s) don't need live data...

In many modern systems masters are used as controllers, that is master's role is only to identify which slave should handle the request.
In other systems, masters do the same work as other replica but an additional task as controllers, in this case, the masters are chosen arbitrarily between one of these replica, and if the master fails, then the replicas choose the new master automatically... (Using something similar to Rock-Paper-Scissors)

## Peer to Peer Architecture

File Sharing Systems such as torrents etc. There is no centralization. Everyone is seeder, everyone is leecher. Load is distributed to all peers.  
Not safe.  

## MVC 
Model–view–controller (MVC) is a software architectural pattern commonly used for developing user interfaces that divide the related program logic into three interconnected elements. This is done to separate internal representations of information from the ways information is presented to and accepted from the user.

Model: The central component of the pattern. It is the application's dynamic data structure, independent of the user interface. It directly manages the data, logic and rules of the application.

View: Any representation of information such as a chart, diagram or table. Multiple views of the same information are possible, such as a bar chart for management and a tabular view for accountants.

Controller: Accepts input and converts it to commands for the model or view.

Good example of seperation of concerns.
Controller has private constructor for empty parameters. However it should take model and view in constructor.

## Event Driven Architecture

Distributed
Asynchronous
Highly scalable
Mediator
Broker