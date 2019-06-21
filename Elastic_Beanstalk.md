
# What is Elastic Beanstalk?

- Elastic Beanstalk is using a PaaS concept.
- Elastic Beanstalk can be used for deploying and scaling web applications. 
- It allows you to upload your code and handles load balancing, logs and metrics management, alerting, application version management, and DNS resolution transparently.

# Architecture

### 1. Elastic Beanstalkdiagram 
![image](https://user-images.githubusercontent.com/5827617/59894809-f6ac6880-941c-11e9-9f1a-9631b0b71a73.png)

- The client sends an HTTP request to the Elastic Beanstalk application. 
- Elastic Beanstalk will then let the deployed application version handle the request and return a response. 
- S3 is used to store different application versions.

### 2. The internals of an Elastic Beanstalk application
![image](https://user-images.githubusercontent.com/5827617/59894851-193e8180-941d-11e9-8ef1-5f1e06cdfb81.png)

- Elastic Beanstalk starts EC2 instances within an Auto Scaling Group and a configurable amount of availability zones. It places the instances inside VPC and configures a security group to protect your instances, by default only accepting connections on port 80.
- Application versions are persisted in a separate S3 bucket and can be imported either directly or from another S3 bucket.
- Elastic Beanstalk supports different platforms, e.g. Java SE, .NET, Node.js, PHP, or Python.
- The domain name is managed through Route 53. Incoming traffic will be send to an Elastic Load Balancer, which acts as an entry point to your application.
-  Elastic Beanstalk will also create Cloud Watch alarms to based on the load of your EC2 instances. (autoscaling alram, monitoring and log management)


# Advantages and Drawbacks

### Advantages
- Lightning Fast Configuration with Automation
- Price and Flexibility

### Drawbacks
- Unreliable Deployment 
- Deployment Speed 
- Stack Upgrades
- Old Application Versions 
