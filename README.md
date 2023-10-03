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
* I set the alarm on Datadog to email when the CPU exceeds 15%. However, I did not receive an email because at the time the cpu did not exceed 15% unless I ran the builds simultaneously . 

### Steps
* Step 1 - Create VPC 
* Step 2 - Create T.2 Medium instance in the public subnet. This allows the instance to receive extra CPU power if needed.
* Step 3 - Install python, nginx, and Jenkins.
* Step 4 - Configured a DataDog agent on the server.
* Step 5 - I had to edit the Jenkins file using get to add a clean stage to the build.
* Step 6 - Setup Alarms to monitor the server in Datadog

### System Diagram
![Deplopyment4](https://github.com/DarrielleEvans/deployApplication/assets/89504317/2a842256-3876-43ba-89c2-212533a24aa2)


### Optimization
I can write a script to build Jenkins and install Python to avoid manually setting up this process each time. 

### Successful Build
<img width="964" alt="Screen Shot 2023-10-02 at 9 40 01 PM" src="https://github.com/DarrielleEvans/deployApplication/assets/89504317/0b19d5b6-c440-4d13-8af9-d9c387229ee5">
<img width="1468" alt="Screen Shot 2023-10-02 at 10 03 26 PM" src="https://github.com/DarrielleEvans/deployApplication/assets/89504317/ed05a343-26af-4752-af09-34418cb08063">

## Server Observation
* The server is performing great. When the builds are ran 1 at a time, the build is successful.
* When I run the builds back to back the CPU spikes above 15%, triggering an alert.
<img width="526" alt="Screen Shot 2023-10-03 at 3 06 01 PM" src="https://github.com/DarrielleEvans/deployApplication/assets/89504317/31daf2b7-dbfb-49b2-bf95-b47bbc982451">
* The application will not perform as expected on a T.2 micro instance when deployed simultaneously . The high cpu usage can cause long build times and unstable applications possibly leading to a poor user experience.
* When the cpu is > 15%, my  team recevies an email of the alert.
<img width="867" alt="Screen Shot 2023-10-03 at 3 38 18 PM" src="https://github.com/DarrielleEvans/deployApplication/assets/89504317/c46ee56b-c126-4b1d-85fb-3bd5c6ca3461">




