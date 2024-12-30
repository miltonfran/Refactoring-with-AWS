<h1>Refactoring with AWS</h1>
 
<h1></h1>

<h2>Description</h2>
This project focuses on rearchitecting or refactoring application services using AWS-managed services. The objective is to replace traditional infrastructure or EC2-based deployments with Platform as a Service (PaaS) and Software as a Service (SaaS) offerings provided by AWS. By adopting this approach, we aim to improve business agility, scalability, and operational efficiency while reducing costs and management overhead.

In this project, we transition from a "lift and shift" strategy to leveraging AWS-managed services like Elastic Beanstalk, Amazon RDS, Elastic Cache, Amazon MQ, Route 53, and CloudFront. The architecture enables seamless scaling, better performance, and a pay-as-you-go model while minimizing administrative tasks.

The final implementation demonstrates hosting a web application stack with automated scaling, monitoring, and content delivery for global users. The project concludes with clean-up operations to optimize resource usage and minimize AWS costs.
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1735526993/Screenshot_2024-12-23_181359_b4wkh2.png"/>
<br />
<h2>Languages and Utilities Used</h2>
Programming Languages: Java (for the application running on Tomcat)
Configuration Files: YAML or JSON for AWS configurations
Utilities: MySQL (via Amazon RDS), Redis (via Elastic Cache)


- <b>Authentication Tools
Google Authenticator (for Multi-Factor Authentication)
Password managers (recommended)</b> 

- <b>Web Browsers
Any modern web browser (Chrome, Firefox, Brave, etc.)</b> 
- <b>Cloud Platform
Amazon Web Services (AWS)
Free Tier Account
Regions (specifically North Virginia)</b>

- <b>AWS Services Used
IAM (Identity and Access Management)
CloudWatch
EC2 (mentioned)
Certificate Manager (ACM)
Simple Notification Service (SNS) </b>


<h2>Tools and Environments Used</h2>

AWS Services:
Elastic Beanstalk (for managing web servers and auto-scaling)
Amazon RDS (for database services)
Elastic Cache (for caching services)
Amazon MQ (for message queueing)
Route 53 (for DNS management)
CloudFront (for Content Delivery Network)
S3 (for storing artifacts)
CloudWatch (for monitoring and alarms)
Development and Build Tools:
Maven or Gradle (for building the application artifacts)
Browsers:
Firefox (for testing CloudFront and caching behavior)
Domain Management:
GoDaddy (for domain setup and DNS entries)



<h2>Program walk-through:</h2>

<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1735527244/Screenshot_2024-12-23_181556_kqmfl1.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1735527185/Screenshot_2024-12-23_182637_vwzv98.png"/>
<br />
<br />
 Setting Up the Environment:

Log in to the AWS Console and create a key pair for secure access.
Set up a security group for backend services like Elastic Cache, RDS, and Amazon MQ.
Create individual backend services (RDS, Elastic Cache, Amazon MQ).
Setting Up Elastic Beanstalk:

Launch an Elastic Beanstalk environment for hosting the application.
Allow traffic between Beanstalk's security group and backend services.
Backend Initialization:

Use an EC2 instance to initialize the RDS database by logging in via MySQL.
Deploying the Application:

Configure application properties with the endpoints for RDS, Amazon MQ, and Elastic Cache.
Build and deploy the application artifact to the Elastic Beanstalk environment.
Configure health checks and HTTPS listeners for the Elastic Load Balancer.
Content Delivery Network:

Set up CloudFront with an SSL certificate for secure connections.
Integrate the application with Route 53 or GoDaddy for domain name resolution.
Testing the Application:

Access the application via a browser and inspect the connection to verify CloudFront integration.
Test application performance, scaling, and operational efficiency.
Cleanup:

Delete all unused AWS resources (CloudFront, RDS, Elastic Cache, Amazon MQ, Elastic Beanstalk) to prevent unnecessary charges.


Architecture Overview
The architecture for this project involves the following components:

Frontend:
CloudFront (for global caching and content delivery)
Route 53 (DNS resolution)
Elastic Load Balancer (managed by Elastic Beanstalk)
S3 bucket (for storing application artifacts)
Backend:
Amazon RDS (relational database)
Elastic Cache (Redis for caching)
Amazon MQ (for message queuing)
Monitoring and Automation:
CloudWatch (for alarms and monitoring)
Auto-scaling (managed by Elastic Beanstalk)
Execution Flow:

The user accesses the application URL via Route 53, resolving to the CloudFront endpoint.
CloudFront forwards the request to an Elastic Load Balancer in the Beanstalk environment.
The load balancer forwards requests to EC2 instances managed by Beanstalk.
Backend services like RDS, Elastic Cache, and Amazon MQ process application data.
CloudWatch monitors the architecture and triggers auto-scaling as needed.


