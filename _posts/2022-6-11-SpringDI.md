---
layout: post
title: Spring Dependency Injection
published: true
---

## Dependency
Dependency is more specific directly relationship among two object, where one of the object modification may require others may need to be modificated.

Coupling is name for a general relationship among object.

Coupling, is degree of dependency.
Lesser dependency means lower coupling.

Below example , both C and B uses object A. C and B both have dependency on type C. C and B is clients of A.
In terms of coupling it is between C and B through A.

If A is modified, both C and B might be modified also. However change in object C most likely does not effect object B.  

There is no dependency between C and B but theres coupling between them.

![Diagram](https://i.ibb.co/b5Hyz2j/coupling-and-dependency-drawio.png))

Client dependent on Service. (A service, BC clients)

## Types of Dependency
- Abstraction  
Client and supplier represent the same concept at different levels of abstraction or from different viewpoints. Commonly called is-a relationship.

- Realization  
Specialized Abstraction dependency between two sets of object, one representing a specification and other reprepesnting an implementation of that specification. 

- Usage  
Client requires service for its full implementation or operation.


## Dependency Injection
## Examples