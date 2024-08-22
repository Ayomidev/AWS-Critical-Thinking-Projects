### Scenario 1: Optimizing Performance and Minimizing Latency Across Regions (India and London)

**Goal**: Design a solution to reduce latency and provide a better browsing experience for users in India and London.

#### Solution Overview:

1. **Content Delivery Network (CDN)**: Use Amazon CloudFront to cache static and dynamic content at edge locations close to users in both regions. CloudFront will distribute traffic efficiently and reduce latency.
2. **Edge Caching**: Leverage edge locations across India and London for caching and quick content retrieval.
3. **Global Load Balancer**: Use AWS Global Accelerator to route traffic based on the lowest latency path. It ensures that users in each region are directed to the closest AWS Region (e.g., Mumbai for India, London for the UK).
4. **Region-Specific Deployments**: Deploy applications in AWS regions close to users—one in Mumbai and one in London. Use Amazon EC2 or AWS Elastic Beanstalk to host the application in each region.
5. **Database Replication**: Set up a database in both regions and use cross-region replication with Amazon RDS to ensure data consistency.

![image](c:\Users\dell\Desktop\Workspace\Pistis Project Repo\Cloud Computing w AWS & GCP)

#### Steps for Implementation:

1. **Set up two AWS Regions**: Mumbai (ap-south-1) and London (eu-west-2).
2. **Use CloudFront**: Create CloudFront distributions with caching at the edge locations closest to the users.
3. **Configure AWS Global Accelerator**: Route traffic to the nearest region using accelerator endpoints for each region.
4. **Deploy Application**: Use EC2 or Elastic Beanstalk to deploy the application in both regions.
5. **Database Replication**: Set up Amazon RDS instances in both regions with cross-region read replicas.

[image](../../../../Pictures/Screenshots)

[image](../../../../Pictures/Screenshots)

[image](../../../../Pictures/Screenshots)

[image](../../../../Pictures/Screenshots)

[image](../../../../Pictures/Screenshots)

[image](../../../../Pictures/Screenshots)

[image](../../../../Pictures/Screenshots)

### Scenario 2: Hosting a Static Website in Amazon S3

**Goal**: Host a static website in an S3 bucket and configure it for high performance and availability.

#### Steps for Implementation:

1. **Create an S3 Bucket**:
   - Go to the S3 console and create a new bucket (e.g., `my-static-website`).
   - Enable "Block all public access" settings as needed and make sure to configure permissions for public read access for website files.
2. **Upload Website Files**:
   - Upload the static files (HTML, CSS, JavaScript) to the S3 bucket.
3. **Enable Static Website Hosting**:
   - In the S3 bucket settings, enable static website hosting by specifying the index and error document (e.g., `index.html` and `error.html`).
4. **Set Permissions**:
   - Configure bucket policies to allow public access to the website.
5. **Configure Domain (Optional)**:
   - If a custom domain is required, configure Route 53 for DNS management and point the domain to the S3 bucket.
6. **Integrate CDN**:
   - Use Amazon CloudFront as a CDN to enhance performance by caching static content globally and improving access times.

#### Architectural Diagram:

Draw an architecture diagram showing the S3 bucket, CloudFront distribution, Route 53 (for domain setup), and user flow.

[image](../../../../Downloads)

After designing, host a sample website in an S3 bucket following the outlined steps.

[image](../../../../Pictures/Screenshots)

[image](../../../../Pictures/Screenshots)

[image](../../../../Pictures/Screenshots)

### Scenario 3: Migrating Legacy Applications to the Cloud

**Goal**: Migrate the legacy application from on-premises to a cloud-native architecture while maintaining the on-premises database.

#### Challenges in On-Premises Infrastructure:

1. **Single Point of Failure**: On-premise setups often have hardware or software components that can fail, leading to system downtime.
2. **Lack of Scalability**: On-prem infrastructure may not scale easily or cost-effectively with increasing demand.
3. **Security Vulnerabilities**: Legacy systems may have outdated security measures, increasing the risk of breaches.
4. **Inefficient Resource Allocation**: Fixed hardware limits make it difficult to efficiently allocate resources to match demand.

#### Proposed Cloud-Native Solution:

1. **Separate Application and Database**:
   - Migrate the application to AWS while keeping the database on-premises to avoid a full migration initially.
   - Use Amazon EC2 or AWS Elastic Beanstalk for application deployment.
2. **Database Connection**:
   - Use AWS Direct Connect or a VPN connection to securely connect the AWS application to the on-premises database.
3. **Security**:
   - Implement AWS Identity and Access Management (IAM) roles and policies to secure the application.
   - Use AWS Web Application Firewall (WAF) for enhanced security.
4. **Eliminate Single Point of Failure**:
   - Deploy the application across multiple Availability Zones to ensure redundancy.
   - Use Auto Scaling and Elastic Load Balancing to handle traffic fluctuations.

#### Architectural Diagram:

- Draw an architecture with the cloud-native application on AWS and a secure connection to the on-premises database.

#### Steps for Implementation:

1. **Deploy Application in AWS**: Use EC2 instances or Elastic Beanstalk for the cloud application.
2. **Setup Direct Connect/VPN**: Establish a secure connection between AWS and the on-premises data center for database communication.
3. **Implement Auto Scaling**: Configure Auto Scaling to ensure the application can handle varying loads.
4. **Secure the Environment**: Implement necessary security measures like IAM, WAF, and encryption.
