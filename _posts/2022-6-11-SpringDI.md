---
layout: post
title: Dependency
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
Client and supplier represent the same concept at different levels of abstraction or from different viewpoints.

- Realization  
Specialized Abstraction dependency between two sets of object, one representing a specification and other reprepesnting an implementation of that specification. 

- Usage  
Client requires service for its full implementation or operation.


In below diagram, A inherits from C and B. Class A extends C implements B. Object A receives an object of D as parameter to its method1. Object A uses object of E as attribute. Object A creates object F.  
![Diagram](https://i.ibb.co/bmBFLLH/coupling-and-dependency-drawio-2.png)  


Abstraction and realization is is-a relationship.  
Abstraction: Implementation inheritance.  
Realization: Interface inheritance.

In Usage dependency, client is incomplete without service so client needs service to operate. This need can be either for definition or implementation.  

For example in above diagram, Class A uses Object D in method1. To execute this method we need Object e. This need is called implementation. Client (A) needs the service (D) only for its implementation of a method. 

For definiton, to define all details of Class A, we need E e object in class A. Client needs service as its part as an instance variable meaning its dependency is for definition.

Dependency for definition is also called Association.(Has-A relationship)

```
public class Student {

    Club[] clubsJoined;

}
```

```
public class Club {

    Student[] studentList;
    
}
```
Association as a relationship has four properties

- Association name (For above example 'Joining')
- Role names of both sides
- Multiplicity (optional, mandatory, single value, multi value, 1-1, 1 to M, M-N)
- Navigability (Uni directonal, bi directional)

![Diagram](https://i.ibb.co/bmBFLLH/coupling-and-dependency-drawio-2.png)  
For example, from same diagram;
- The object of A owns object of E,
- Object of A receives object of D as uses d as parameter of its method
- Object of A creates object of F.

For the first one, there s an association between Object of A and E.
Other two is implementation dependency.


Association has two types.
- Aggregation: Object is used to group other objects.
- Composition: Strong form of aggregation that requires a part of object to be included in at most one composite object at a time. 

A tree is a composition of its root, trunk and leaves.


