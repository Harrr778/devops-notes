source: https://www.geeksforgeeks.org/amazon-web-services-scaling-amazon-ec2/
## Auto Scaling

Auto Scaling is a feature in cloud computing that allows a cloud-based application to automatically adjust the resources it uses such as servers, compute instances based on demand. The goal of Auto Scaling is to ensure that the application has sufficient resources to meet performance goals and maintain availability, while also optimizing resource utilization and minimizing costs. To know the difference between Auto scaling and load balancer refer to the [Auto Scaling vs Load Balancer](https://www.geeksforgeeks.org/auto-scaling-vs-load-balancer/).

# AWS(Amazon Web Services) Auto Scaling

AWS auto-scaling is used to scale up and scale down the EC2-instance by depending on the incoming traffic. You can scale up and scale down the applications in a few minutes based on the traffic which will decrease the latency of the application to the end-users.

# Benefits of Auto Scaling

***Dynamical scaling:*** AWS auto-scaling service doesn’t require any type of manual intervention it will automatically scale the application down and up by depending up on the incoming traffic.
- ****Pay For You Use:**** In auto scaling the resource will be utilised in the optimised way where the demand is low the resource utilisation will be low and the demand will high the resource utilisation will increase so the AWS is going to charge you only for the amount of resources you really used.
- ****Automatic Performance Maintenance:**** AWS auto scaling maintains the optimal application performance with considering the workloads it will ensures that the application is running to desired level which will decrease the latency and also the capacity will be increased by based on your application

## Auto Scaling Components

Following are the components of AWS Scaling Components.

- ****Groups:****For scaling and managing the EC2 instances are grouped together so that they may be thought of as a single logical entity. You can mention the minimum and maximum no.of EC2 instance are required based up on the demand of the incoming traffic.
- ****Configuration templates:**** Configuration template or an launch template which is used by the EC2 autoscaling group for the EC2 instance. In which you can specify the Amazon Machine Image ID,keypair,security group and so on.
- ****Scaling options: Aws Autoscaling provides no.of options some of them are mentioned as following.****
    - Dynamic scaling
    - Predictive scaling
    - Scheduled scaling
    - Manual scaling

![Auto-Scaling EC2](https://media.geeksforgeeks.org/wp-content/uploads/20230828125811/Auto-Scaling---ec2.png)

That’s the point where Amazon EC2 Autoscaling comes into the picture. You may use Amazon EC2 Auto Scaling in order to add or delete Amazon EC2 instances with respect to changes in your application demand. You can maintain a higher feeling of application availability by dynamically scaling your instances in and out as needed.

## Features Of AWS (Amazon Web Services) Auto Scaling

You can use three scaling techniques within Amazon EC2 Auto Scaling i.e. Dynamic Scaling, Predictive Scaling, and Scheduled Scaling. They are explained in detail below:

- ****Dynamic Scaling: A****dapts to changing environments and responds with the EC2 instances as per the demand. It helps the user to follow the demand curve for the application, which ultimately helps the maintainer/user to scale the instances ahead of time. Target tracking scaling policies, for example, may be used to choose a loaded statistic for your application, such as CPU use. Alternatively, you might use Application Load Balancer’s new “Request Count Per Target” measure, which is a load balancing option for the Elastic Load Balancing service. After that, Amazon EC2 Auto Scaling will modify the number of EC2 instances as needed to keep you on track. 

- ****Predictive Scaling:**** Helps you to schedule the right number of EC2 instances based on the predicted demand. You can use both dynamic and predictive scaling approaches together for faster scaling of the application. Predictive Scaling forecasts future traffic and allocates the appropriate number of EC2 instances ahead of time. Machine learning algorithms in Predictive Scaling identify changes in daily and weekly patterns and automatically update projections. In this way, the need to manually scale the instances on particular days is relieved. 

- ****Scheduled Scaling:**** As the name suggests allows you to scale your application based on the scheduled time you set. For e.g. A coffee shop owner may employ more baristas on weekends because of the increased demand and frees them on weekdays because of reduced demand.

Computing power is a programmed resource in the cloud, so you may take a more flexible approach to scale your applications. When you add Amazon EC2 Auto Scaling to an application, you may create new instances as needed and terminate them when they’re no longer in use. In this way, you only pay for the instances you use, when they’re in use.

## Types Of AWS (Amazon Web Services) Autoscaling

- ****Horizontal Scaling:**** [Horizontal scaling](https://www.geeksforgeeks.org/horizontal-and-vertical-scaling-in-databases/) involves adding more instances to your application to handle increased demand. This can be done manually by launching additional instances, or automatically using Amazon EC2 Auto Scaling, which monitors your application’s workload and adds or removes instances based on predefined rules.
- ****Vertical Scaling:**** [Vertical scaling](https://www.geeksforgeeks.org/horizontal-and-vertical-scaling-in-databases/) involves increasing the resources of existing instances, such as CPU, memory, or storage. This can be done manually by resizing instances, or automatically using Amazon EC2 Auto Scaling with launch configurations that specify instance sizes based on the workload.
- ****Load Balancing:**** Load balancing involves distributing incoming traffic across multiple instances to improve performance and availability. [Amazon Elastic Load Balancing (ELB)](https://www.geeksforgeeks.org/elastic-load-balancer-in-aws/) is a service that automatically distributes incoming traffic across multiple instances in one or more Availability Zones.
- ****Multi-Availability Zone Deployment:**** Multi-Availability Zone (AZ) deployment involves launching instances in multiple AZs to improve availability and fault tolerance. Amazon EC2 Auto Scaling can be used to automatically launch instances in additional AZs to maintain availability in case of an AZ outage.
- ****Containerization:**** [Containerization](https://www.geeksforgeeks.org/containerization-using-docker/) involves using containers to package and deploy applications, making them more portable and easier to manage. [Amazon Elastic Container Service (ECS)](https://www.geeksforgeeks.org/introduction-to-amazon-elastic-container-service-ecs/) is a service that makes it easy to run, stop, and manage Docker containers on a cluster of EC2 instances.



> [!NOTE]
> When we created the auto-scaling group, we configured the Desired capacity, Minimum capacity, maximum capacity, and CPU utilization. If CPU utilization increases by 60% in all instances, one more instance is created, and if CPU utilization decreases by 30% in all instances, one instance is terminated.

## AWS Auto Scaling – FAQ’S

### 1. What Is The Difference Between AWS Auto Scaling And EC2 Auto Scaling?

> AWS auto scaling is an service provided by the AWS which is used to scale the EC2 by depending up the in coming traffic.

### 2. What Are The Two Types Of Auto Scaling?

> Auto scaling is mainly used to scale up and scale down the application based on the load. There are four main types of AWS autoscaling:
> 
> 1. manual scaling,
> 2. scheduled scaling,
> 3. dynamic scaling, and
> 4. predictive scaling

### 3. What Are The 3 Components Of Auto Scaling Group?

> The main components of autoscaling was mentioned below.
> 
> 1. Load Balancer.
> 2. Snapshot.
> 3. EC2 (Elastic Compute Cloud) Instance.
> 4. Autoscaling group.

### 4. AWS Autoscaling Group Terraform

> AWS Auto Scaling Group Terraform is a module that allows you to create and manage Auto Scaling groups using Terraform.