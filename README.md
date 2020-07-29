# Microservices Notes for Training

## Course Contents
![Mind Map](https://github.com/pratikdas/MSA_Training_Jul_20/blob/master/_assets/images/Microservice-MindMap.png)

## Motivations
We traditionally built 


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
