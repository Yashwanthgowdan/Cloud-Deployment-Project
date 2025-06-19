# Cloud-Deployment-Project
This project involves deploying the MERN-based Travel Memory app on Amazon EC2. It focuses on full-stack cloud deployment, backend and frontend configuration, and building a scalable architecture using tools like AWS Load Balancer and Cloudflare.

The TravelMemory application is a full-stack web application built with the MERN (MongoDB, Express.js, React, Node.js) stack. This project primarily focuses on deploying the application on an Amazon EC2 instance, ensuring seamless integration between front end and back end, scalability via load balancing, and custom domain setup through Cloudflare.

Project Repository: https://github.com/UnpredictablePrashant/TravelMemory

Objectives or goals of this project:
1. Creating EC2 instances and MongoDB.
2. Configuring the backend and connecting it with a MongoDB instance.
3. Configuring frontend and linking it to the backend.
4. Implementing load balancing to divide traffic.
5. Integrating a custom domain using Cloudflare.

1. Creating EC2 instances and MongoDB.
   >Creating EC2 Instances:
    1. Log in to AWS Management Console.
    2. Navigate to EC2 Dashboard and click "Launch Instance".
    3. Choose Ubuntu Server as the OS, instance type and key pair for SSH access.
    4. Configure Security Group to allow ports 22 (SSH), 80 (HTTP), 443 (HTTPS), and 3000 (backend).
    5. Launch the instance.
    Reapet the same steps to again one instance for Backend and one for Front end.

   >Setting Up MongoDB:
    1. Sign up and log in to MongoDB Atlas.
    2. Create a new project and build a free-tier cluster.
    3. Create a database user with username and password.
    4. Connect to DB on MongoDB Compass.
    5. Obtain the connection string (MongoDB URI).

2. Configuring the backend and connecting it with a MongoDB instance.
   1. Connect to the backend instance using SSH with the key pair.
   2. Clone the Repository:                 git clone https://github.com/Yashwanthgowdan/TravelMemory.git
   3. Jump to Backend directory:            cd TravelMemory/backend/
   4. Create .env to connect to DB:         sudo nano .env
   5. Enter Mongo DB URI:                   MONGO_URI='ENTER_YOUR_URL' PORT=3001
   6. Install Node.js:                      sudo apt install nodejs -y
   7. Install packages:                     sudo npm install
   8. Run Node.js application:              sudo node index.js
    ![image](https://github.com/user-attachments/assets/e2b92c43-4af0-45da-986e-5594917d3f73)

3. Configuring frontend and linking it to the backend.
   1. Connect to the frontend instance using SSH with the key pair.
   2. Clone the Repository:                  git clone https://github.com/Yashwanthgowdan/TravelMemory.git
   3. Jump to Frontend directory:            cd TravelMemory/frontend/
   4. Create .env to connect to DB:          sudo nano .env
   5. Enter Backend public IP to link both:  REACT_APP_BACKEND_URL=http://localhost:3001
   6. Install packages:                      sudo npm install
   7. Start application:                     sudo npm start
    ![image](https://github.com/user-attachments/assets/9219fe27-1f02-4c3c-85fe-6d4c7f11972f)

4. Implementing load balancing to divide traffic.
    1. Creat AMI template images for both the frontend and backend instances, then launch new instances from these templates.
    2. Create Target groups for both backend and frontend instaces seperately.
    3. Navigate to AWS Elastic Load Balancer (ELB) and select Create Load Balancer.
    4. Attach the target groups to the Load Balancer listener on port 80.
    5. Configure Health checks to ensure traffic only routes to healthy instances.
    6. Verify the setup by accessing the ELB DNS name to confirm load-balanced access to the application.
    ![image](https://github.com/user-attachments/assets/66d117e5-f39b-4b8c-804a-2a0227bd503a)

  
5. Integrating a custom domain using Cloudflare.
    1. Purchased the domain: yashwanth.store from https://www.namecheap.com/
    2. Linked the domain with Cloudflare by updating Namecheap's nameservers to Cloudflare's.
    3. Created a CNAME record in Cloudflare, pointing the domain to the AWS ELB DNS name.
    4. Created an SSL certificate using AWS Certificate Manager (ACM) and attached it to the Elastic Load Balancer to enable HTTPS via Cloudflare's SSL/TLS settings.
       ![image](https://github.com/user-attachments/assets/4a1f31b4-84e4-4811-afd1-e0b9a3b060a2)

Application working Screenshots:
  With Domain:
  ![image](https://github.com/user-attachments/assets/f7dda3d7-ec77-4cf0-96e6-177791e0803e)

  With SSL Certificate:
  ![image](https://github.com/user-attachments/assets/38a8f2af-bf83-4467-b0f8-7fe3884bbb48)

  Data stored in DB:
  ![image](https://github.com/user-attachments/assets/8ba6962d-197a-4bb6-b77c-a49535baa70a)

Deployment architecture diagram to visualize the flow and connections:
  ![Untitled Diagram drawio](https://github.com/user-attachments/assets/3edba233-0f36-4098-8ff6-14a095409a41)



