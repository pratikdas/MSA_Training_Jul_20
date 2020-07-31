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

## Transactions
### Eventual vs strongly consistent

### CAP Theorem
The CAP theorem states that a distributed system can deliver only two of the three desired characteristics: consistency, availability, and partition tolerance. 

The CAP theorem helps to chhose an appropriate database when designing a distributed system like microservice.
For example, if the ability to quickly iterate the data model and scale horizontally is essential to your application, but you can tolerate eventual consistency, an AP database like Cassandra or Apache CouchDB can meet your requirements and simplify your deployment. On the other hand, if your application depends heavily on data consistency—as in an eCommerce application or a payment service—you might opt for a relational database like PostgreSQL.

## Deployment Options


### 1 host per service
Deploy in VM

### 1 host many services - Containers
####Build Docker Images
Docker builds images automatically by reading the instructions from a Dockerfile -- a text file that contains all commands, in order, needed to build a given image. A Dockerfile adheres to a specific format and set of instructions which you can find at Dockerfile reference.

A Docker image consists of read-only layers each of which represents a Dockerfile instruction. The layers are stacked and each one is a delta of the changes from the previous layer. Consider this Dockerfile:

```
FROM ubuntu:18.04
COPY . /app
RUN make /app
CMD python /app/app.py
Each instruction creates one layer:
```

FROM creates a layer from the ubuntu:18.04 Docker image.
COPY adds files from your Docker client’s current directory.
RUN builds your application with make.
CMD specifies what command to run within the container.

When you run an image and generate a container, you add a new writable layer (the “container layer”) on top of the underlying layers. All changes made to the running container, such as writing new files, modifying existing files, and deleting files, are written to this thin writable container layer.

#### Build Context
When you issue a docker build command, the current working directory is called the build context. By default, the Dockerfile is assumed to be located here, but you can specify a different location with the file flag (-f). Regardless of where the Dockerfile actually lives, all recursive contents of files and directories in the current directory are sent to the Docker daemon as the build context.

#### Add .dockerignore
```
# ignore all files under temp folder
*/temp/*
```

#### Useful Commands
Clean
```
docker system prune -a
```
List all images
```
docker images -a 
```
Delete all images
```
docker rmi <imageid>
```

Docker Build
```
docker build . --tag <name>:v1
```
Docker run (it for interactive)
```
docker run -it -p8080:8080 userreg1:v1
```
docker start, stop 

### Container Orchestration

Kubernetes is most widely used orchestration tool. 
The main theme is of Kubernetes is - 
1. Describe the desired state of the container declaratively in a yaml file.
2. Apply the desired state to the cluster.
3. Maintain the actual state in sync with the desired state.
4. State is in simple terms the number of container instances running in the cluster.

Useful kubectl Commands:

kubectl apply -f <filename.yaml>
For hands-on follow the steps in this course:
https://www.katacoda.com/courses/kubernetes/creating-kubernetes-yaml-definitions
For microservice deployment we usually create 2 objects:
1. Deployment: deployment.yaml which in turn creates a replicaset. The replicaset object is responsible for maintaining the synchronization between actual and desired state that is the number of pods in the cluster. 
2. Service: Nodeport service will expose the url of the service for accessing the microservice running inside the container.


### Serverless Options
On-demand provisioning: Provision the infrastructure resources at the time of serving the request.
No servers to manage.
Billing depends on application execution metrics during request processing.

Available services: 
1. AWS Lambda
2. Azure Function
3. Google Cloud Function
4. On going projects under CNCF like FAAS and knative

