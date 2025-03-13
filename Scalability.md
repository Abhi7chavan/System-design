# Scalability

Scalability is the property of a system that allows it to handle increasing load by adding resources. The need for scalability arises due to:

- **More users** → Increased traffic.
- **More features** → Higher computational demands.
- **More geographical locations** → Need for global access.
- **More complexity** → More dependencies and interactions.

## Types of Scalability

### **1. Vertical Scaling (Scaling Up)**

Involves adding more resources (CPU, RAM, storage) to an existing machine.

#### **Pros:**
- Higher data consistency (since everything runs on a single machine).
- Fast inter-process communication (IPC).
- No need for load balancing.

#### **Cons:**
- Expensive compared to horizontal scaling.
- Hardware limitations (you can scale up only so much).
- Single point of failure (if the machine crashes, the system goes down).

### **2. Horizontal Scaling (Scaling Out)**

Involves adding multiple servers to distribute the load.

#### **Pros:**
- Less expensive than vertical scaling.
- No hardware limitations (can scale infinitely by adding more machines).
- Resilient (if one server fails, others can handle the load).

#### **Cons:**
- Requires load balancing to distribute traffic.
- Uses RPC (Remote Procedure Calls) for communication.
- Data inconsistency can occur due to distributed architecture.

## **Key Differences**

| **Aspect**           | **Vertical Scaling**                  | **Horizontal Scaling**                  |
|----------------------|--------------------------------|--------------------------------|
| **Scaling method**   | Add resources to a single machine | Add more machines to distribute load |
| **Cost**            | Expensive                      | Less expensive |
| **Load Balancing**  | Not needed                     | Required |
| **Communication**   | Fast IPC                        | RPC-based (slower) |
| **Failure Handling**| Single point of failure         | Resilient |
| **Scalability Limit** | Hardware limits               | No limits |

## **AWS Services for Scaling**

### **1. Vertical Scaling (Scaling Up)**
- **AWS EC2 (Elastic Compute Cloud)** allows you to dynamically resize an instance by upgrading the CPU, RAM, or storage.
- You can stop an EC2 instance, change the instance type (e.g., `t2.medium → t2.large`), and restart it.
- **Example:** If a database server is struggling with load, you can increase the instance size to improve performance.
- **Limitation:** There is a max instance size, so it **doesn’t scale indefinitely**.

### **2. Horizontal Scaling (Scaling Out)**
- **AWS Elastic Load Balancer (ELB) + Auto Scaling Groups (ASG)** distribute traffic across multiple instances.
- **Elastic Kubernetes Service (EKS) & Elastic Container Service (ECS)** handle containerized applications.
- **Example:** A web application serving millions of users can scale horizontally by adding more EC2 instances behind a load balancer.
- **Benefit:** More resilient—if one machine fails, others take over.

## **Key AWS Services for Scaling**

| **Scaling Type**    | **AWS Services** |
|---------------------|-----------------|
| **Vertical Scaling** | EC2 instance resizing, RDS vertical scaling |
| **Horizontal Scaling** | ELB + Auto Scaling, ECS, EKS, DynamoDB auto-scaling |
