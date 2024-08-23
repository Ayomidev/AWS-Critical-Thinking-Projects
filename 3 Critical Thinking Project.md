This critical thinking project covers implementing **dynamic scaling using AWS Auto Scaling** to handle traffic surges and optimize resource usage for an e-commerce website.

### **1. Understand the Given Architecture Diagram**

- The architecture includes components such as:
  - A **Load Balancer (ELB)** to distribute traffic across instances.
  - An **Auto Scaling Group (ASG)** to dynamically manage EC2 instances based on traffic.
  - Multiple **Availability Zones (AZs)** in a single region to ensure high availability and fault tolerance.
  - A **Node.js Application** running on EC2 instances.

### **2. Create the Infrastructure**

- **VPC**: Ensure a Virtual Private Cloud is set up with subnets across multiple Availability Zones.
- **Auto Scaling Group (ASG)**: Configure the ASG to manage EC2 instances dynamically based on demand.
- **Load Balancer (ALB or NLB)**: Use an Application Load Balancer to route traffic to the instances.
- **Launch Template**: Define the instance configuration (AMI, instance type, security groups, etc.) for your ASG.

![image](<Screenshot (214).png>)

### **3. Ensure Your Infrastructure is Split Across Multiple Zones in a Single Region**

- In the VPC, configure **subnets** across at least two Availability Zones within a region to ensure fault tolerance.
- Attach the **Auto Scaling Group** to these subnets so that instances can launch in multiple zones.

![image](<Screenshot (215).png>)

![image](<Screenshot (216).png>)

### **4. Deploy a Simple Node.js Application to the Infrastructure**

- Install Node.js on the EC2 instances as part of the **user data script** in the launch template.
- Deploy a simple Node.js app, e.g., a "Hello World" app, and ensure it's available via the load balancer's DNS endpoint.

### **5. Load Test the Application**

Use a tool like **Apache JMeter**, **Artillery**, or **Locust** to simulate high traffic to the application. This will trigger load-based scaling and validate your infrastructure's ability to handle increased traffic.

![image](<Screenshot (220).png>)

### **6. Ensure Auto Scaling Based on CPU Usage**

- Configure **CloudWatch Alarms** to monitor CPU utilization of your instances.
- Set a scaling policy in the ASG to add instances when CPU utilization exceeds **80%**.
  - For example, when the alarm is triggered, the ASG should add a defined number of instances to meet the demand.

![image](<Screenshot (221).png>)

### **7. Ensure Auto Scaling Based on Memory Usage**

- Since **CloudWatch** doesn't monitor memory by default, install the **CloudWatch Agent** on each EC2 instance to send memory usage metrics to CloudWatch.
- Create a similar **CloudWatch Alarm** to trigger scaling when memory usage exceeds **80%**.

### **8. Ensure the Auto-Scaling Group Scales Down When Load Decreases**

- Configure another **CloudWatch Alarm** to monitor when CPU/memory utilization falls below a certain threshold (e.g., 50%) to remove instances and scale down.
- The scaling policy should terminate instances when they are no longer needed, minimizing costs.

### **9. Delete All Resources After You Are Done**

- Ensure you delete all resources once testing is complete. This can be done via the AWS Management Console, or by automating resource cleanup using CloudFormation/Terraform **deletion policies**.

### **Key AWS Services Used**

- **EC2**: Hosting your Node.js app
- **Auto Scaling Group**: Automatically scaling EC2 instances
- **Elastic Load Balancer**: Distributing traffic
- **CloudWatch**: Monitoring metrics for CPU, memory, and creating alarms
- **CloudWatch Agent**: Sending memory metrics to CloudWatch
