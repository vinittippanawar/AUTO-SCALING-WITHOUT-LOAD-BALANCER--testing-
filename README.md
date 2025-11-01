# 🧠 AUTO-SCALING-WITHOUT-LOAD-BALANCER-TESTING-
Hands-on project demonstrating AWS Auto Scaling without a Load Balancer — using EC2, AMI, Launch Template, and Auto Scaling Group to achieve high availability and fault tolerance.
### 1.💡Launch EC2 Instance
- OS: Ubuntu  
- Created or selected a key pair for SSH access.  
- Enabled **Auto-assign Public IP**.  
- Created a new Security Group named `launch-wizard-6'-
- Edited **Inbound Rules**:  
  - Type: HTTP  
  - Source: Anywhere (IPv4)  

---

### 2. 🛠️Configure EC2 and Deploy Nginx
- Connected via PowerShell:  
  ```bash
  ssh -i <path_to_keypair> ubuntu@<public_ip>
  ```
- Updated packages and installed Nginx:  
  ```bash
  sudo apt-get update
  sudo apt-get install nginx -y
  sudo systemctl start nginx
  sudo systemctl enable nginx.service
  ```
- Replaced the default web file:  
  ```bash
  cd /var/www/html
  sudo rm index.nginx-debian.html
  sudo nano index.html
  ```
  Added:
  ```html
  <h1>Welcome to Auto scaling</h1>
  ```
- Verified the web page by hit  `http://<public_ip>` in a browser.

---

### 3.🧩 Create an AMI
- Selected the EC2 instance → **Actions → Image and Templates → Create Image**.  
- Named and created the AMI.  
- Waited until status became **Available**, then terminated the original instance.

---

### 4.📝 Create Launch Template
- Created a new **Launch Template**.  
- Go to Application and OS Images (Amazon Machine Image) and Select My AMIs
- Instance Type: `t2.micro` (or chosen type).  
- Selected the same Key Pair and Security Group (`launch-wizard-6`).

---

### 5.🛠️Configure Auto Scaling Group (ASG)
- Created an **Auto Scaling Group** linked to the Launch Template.  
- Selected 2 or more **Subnets** .  
- Skipped the Load Balancer configuration. (select no load balancer) 
- Updated **Health Check Grace Period** from `300s` to `30s`.  
- Accepted default scaling settings and launched the ASG.

---

### 6.💡Testing Auto Scaling
- Verified that the ASG automatically launched an instance.  
- Terminated the instance manually and confirmed a new one was created automatically within ~30 seconds.

---

## 🧩 Key Points
- Demonstrated EC2 setup and configuration.  
- Created and used a custom AMI for scaling.  
- Implemented Auto Scaling functionality **without a Load Balancer**.  
- Understood fault tolerance and automated recovery in AWS.

---

## 🛠️ Technologies Used
- AWS EC2
- Amazon Machine Image (AMI)
- Launch Template
- Auto Scaling Group
- Ubuntu + Nginx

---## ✍️Author
**Vinit Tippanawar**  
Cloud Computing Enthusiast | AWS Learner  


