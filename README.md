# Microservices Notes for Training

## Course Contents
![Mind Map](https://github.com/pratikdas/MSA_Training_Jul_20/blob/master/_assets/images/Microservice-MindMap.png)

## Key Takeaways
By the end of this course, participants will be able to:

1. Understand when to use and when not to use microservice architecture.
2. Decompose an application into microservices using Domain Driven Design.
3. Apply design patterns for building a microservice application.
4. Understand Microservice deployment options using a container, PAAS platforms, and serverless technologies
5. Identify and choose their area of interest for deep dive.
6. Refactor a monolithic application into Microservices. 

## Motivations
We traditionally built monolithic applications where we bundle all functionality of an application in a single deployment unit. When application size is small, this solution is preferable since it is easy to manage and deploy. Once the application becomes big it becomes difficult to change. We are worried about the impact any change might make to other parts of the applications. Also for scaling, we need to scale the complete application instead of any single function which is frequently used.


## What is Microservice
A logical component with some of the below characteristics:
1. Focussed on the business domain
2. A single unit of cohesive functions
3. Decoupled from other microservices
4. Independently Deployable
5. Small Autonomous Teams
6. Culture of Automation
7. Highly Observable


## Designing a Microservice Application 

The first step is the decomposition of a system into microservices. Domain-Driven Design (DDD) is a method of decomposition by using bounded contexts.

A Microservice Application has an inner architecture which is the architecture of an individual microservice and an outer architecture governing the communication between the microservices.

Inner Architecture is simple with popular tech stacks available from the community called a chassis. The 
The complexity has moved to the outside. 

### Case Study
 An e-commerce application like amazon or eBay having a storefront that customers visit to select from a range of products and buy items of their choice. 

### User Story 1
Customer registers by providing his/her email. The application sends a confirmation email with a confirmation link to verify the email address. The customer will visit this link to confirm. The system will activate the account. The customer can login with email and password.

### User Story 2
The products displayed in the online store are mantained in Inventory Microservice. Orders are managed by the Orders Microservice and Items placed in the shopping cart are managed by the Cart microservice.


### Communication Styles
1. Synchronous
REST API
2. Asynchronous
Messaging Middleware
Queue
Publish-Subscribe
3. Client-Service Communication with API Gateway
4. Service-Service Communication with Service Mesh



### Tradeoffs using CAP Theorem
The CAP theorem puts a constraint on addressing only any two of Consistency, Availability, and Partitioning.

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
