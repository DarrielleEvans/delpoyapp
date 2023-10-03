## Purpose
The purpose of the project is to deploy an application on an EC2.

I used Elastic Beanstalk to deploy the URL Shortener Application in previous deployments. In this deployment, we chose to use NGINX instead of Elastic Beanstalk. 
This setup allows us more customization configurations and uses less memory while performing on a larger scale.

## Technologies Used
* VPC
* Jenkins Server
* GitHub
* NGINX
* AWS EC2
* Subnets
* Datadog
* Python

### Issue
* I was denied permission when accessing/etc/nginx/sites-enabled/default. I used sudo nano default to access the file using the superuser.
* I set the alarm on Datadog to email when the CPU is higher than 15%. However, I have yet to receive an email.

### Steps
* Step 1 - Create VPC 
* Step 2 - Create T.2 Medium instance in the public subnet. This allows the instance to receive a burst of extra CPU power if needed.
* Step 3 - Install python, nginx, and Jenkins.
* Step 4 - Configured a DataDog agent on the server.
* Step 5 - I had to edit the Jenkins file using get to add a clean stage to the build.
* Step 6 - Setup Alarms to monitor the server in Datadog

### System Diagram

<img width="964" alt="Screen Shot 2023-10-02 at 9 40 01 PM" src="https://github.com/DarrielleEvans/deployApplication/assets/89504317/ce7a2939-516b-4ba9-9248-51b4bf53a160">

### Optimization
I would write a script to build Jenkins and install Python to avoid manually setting up this process each time.

### Successful Build
<img width="964" alt="Screen Shot 2023-10-02 at 9 40 01 PM" src="https://github.com/DarrielleEvans/deployApplication/assets/89504317/0b19d5b6-c440-4d13-8af9-d9c387229ee5">
<img width="1468" alt="Screen Shot 2023-10-02 at 10 03 26 PM" src="https://github.com/DarrielleEvans/deployApplication/assets/89504317/ed05a343-26af-4752-af09-34418cb08063">
