Deploy Web Server on AWS Lambda and Elastic BeanStalk

### 1. **Understand the Project**

- **Objective:** Deploy a static website on AWS Lambda and Elastic Beanstalk, compare their performance, scalability, and cost, and ensure resources are deleted afterward.
- **Scope:**
  - Obtain a static website template.
  - Deploy it on AWS Lambda and Elastic Beanstalk.
  - Compare the performance, scalability, and costs.
  - Clean up resources.

### 2. **Obtain a Static Website Template**

1. **Find a Template:**

   - Search for a simple static website template online.
   - Ensure the template includes HTML, CSS, and JavaScript files.

2. **Download the Template:**
   - Download the files and organize them into a folder for easy access.

### 3. **Deploy the Web Server on AWS Lambda**

1. **Set Up Lambda Function:**

   - Create an AWS Lambda function.
   - Choose a runtime that supports serving HTTP requests, such as Node.js or Python.
   - Write a function to serve your static website files. You might use AWS API Gateway to route HTTP requests to your Lambda function.

2. **Deploy the Static Website:**

   - Upload your website files to an S3 bucket.
   - Configure Lambda to fetch files from S3 and respond to HTTP requests.

3. **Test the Deployment:**
   - Access the URL provided by API Gateway and verify that your website is served correctly.

![image](<Screenshot (240).png>)

![image](<Screenshot (234).png>)

![image](<Screenshot (238).png>)

![image](<Screenshot (239).png>)

![image](<Screenshot (241).png>)

### 4. **Deploy the Web Server on Elastic Beanstalk**

1. **Set Up Elastic Beanstalk Environment:**

   - Create a new Elastic Beanstalk environment.
   - Choose the appropriate platform (e.g., Node.js or Python for a static site).
   - Prepare your website files for deployment (usually as a .zip file).

2. **Deploy the Static Website:**

   - Upload the .zip file to Elastic Beanstalk.
   - Elastic Beanstalk will handle the deployment and provisioning of resources.

3. **Test the Deployment:**
   - Access the URL provided by Elastic Beanstalk and ensure your website is functioning correctly.

![image](<Screenshot (243).png>)

![image](<Screenshot (244).png>)

![image](<Screenshot (245).png>)

### 5. **Performance and Scalability Comparison**

1. **Monitor Performance:**

   - Use AWS CloudWatch to monitor performance metrics such as response time, error rates, and resource usage for both Lambda and Elastic Beanstalk.

2. **Scalability Testing:**

   - Test how each solution scales by simulating traffic spikes using tools like Apache JMeter or AWS’s own tools.

3. **Analyze Results:**
   - Compare response times, handling of concurrent requests, and resource utilization between Lambda and Elastic Beanstalk.

### 6. **Analyze Cost Implications**

1. **Review Cost Reports:**

   - Use AWS Cost Explorer to analyze the costs associated with Lambda and Elastic Beanstalk.
   - Compare the costs based on your traffic and resource usage.

2. **Consider Factors:**
   - For Lambda: Costs are based on execution time and memory usage.
   - For Elastic Beanstalk: Costs include EC2 instances, load balancers, and data transfer.

### 7. **Clean Up Resources**

1. **Delete Lambda Function and API Gateway:**

   - Go to the AWS Lambda console and delete the function.
   - Remove the API Gateway configuration.

2. **Delete S3 Bucket:**

   - Ensure you delete the S3 bucket where the static website files were stored.

3. **Terminate Elastic Beanstalk Environment:**

   - Go to the Elastic Beanstalk console and terminate the environment.

4. **Confirm Resource Deletion:**
   - Verify that all resources (Lambda, S3, Elastic Beanstalk) are deleted and no charges are incurred.
