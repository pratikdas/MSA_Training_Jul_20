# Microservices Notes for Training

## Course Contents
![Mind Map](https://github.com/pratikdas/MSA_Training_Jul_20/blob/master/_assets/images/Microservice-MindMap.png)

## Key Takeaways
By the end of this course, participants will be able to:

1. Understand when to use and when not to use microservice architecture.
2. Decompose an application into microservices using Domain Driven Design.
3. Apply design patterns for building a microservice application.
4. Under Microservoce deployment options using container, PAAS platforms and serverless technologies
5. Identify and choose their area of interest for deep dive.
6. Refactor a monolithic application into Microservices. 

## Motivations
We traditionally built monolithic applications where we bundle all functionality of an application in a single deployment unit. When application size is small, this solution is preferable since it is easy to manage and deploy. Once application becomes big it becomes difficult to change. We are worried about the impact any change might make to other parts of the applications. Also for scaling, we need to scale the complete application instead of any single function which is frequently used.


## What is Microservice
A logical component with some of the below characteristics:
1. Focussed on business domain
2. Single unit of cohesive functions
3. Decoupled from other microservices
4. Independently Deployable
5. Small Autonomous Teams
6. Culture of Automation
7. Highly Observable


## Designing a Microservice Application 

First step is decomposition of a system into microservices. Domain Driven Design (DDD) is a method of decomposition by using bounded contexts.

A Microservice Application has an inner architecture which is the architecture of an individual microservice and an outer architecture governing the communication between the microservices.

Inner Architecture is simple with popular tech stacks available from the community called a chassis. The 
The complexity has moved to the outside. 

### Case Study
 A e-commerce application like amazon or ebay having a storefront which customers visit to select from a range of products and buy items of their choice.  

### Communication Styles
1. Synchronomous
REST API
2. Asynchronous
Messaging Middleware
Queue
Publish-Subscribe
3. Client-Service Communication with API Gateway
4. Service-Service Communication with Service Mesh



### Tradeoffs using CAP Theorem
The CAP theorem puts a constraint on addressing only any two of Consistency, Availability and Partitioning.

### Handle Failures 
1. Circuit Breaker
2. Throttling
3. Bulkhead
4. Chaos Engineering

## Deployment Options

### 1 host per service

### 1 host many services - Containers

### Container Orchestration

### Serverless Options
