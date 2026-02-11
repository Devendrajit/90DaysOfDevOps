# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

## Goal
Deploy a real web server on the cloud and practice **production-level DevOps tasks** such as server provisioning, secure access, service deployment, security configuration, and log extraction.

---

## Part 1: Launch Cloud Instance & SSH Access

### Step 1: Create a Cloud Instance
- Created a Linux virtual machine using **AWS EC2 (Ubuntu 22.04)**
- Selected a free-tier eligible instance
- Generated and downloaded an SSH key pair
- Configured security rules to allow:
  - **SSH (Port 22)**
  - **HTTP (Port 80)**
<img width="1361" height="302" alt="image" src="https://github.com/user-attachments/assets/2dee4043-8045-4d57-9b87-b3cbe2dd6037" />
---

### Step 2: Connect to Server via SSH

```bash
ssh -i "my-wbsvr-key.pem" ubuntu@ec2-34-228-19-69.compute-1.amazonaws.com
```
### SSH Connection to Cloud Server
<img width="1362" height="659" alt="image" src="https://github.com/user-attachments/assets/efb51adf-3ea2-4f7f-884a-e54c4a0374d5" />




<p align="center">
  <b>Figure:</b> Successful SSH connection to cloud instance
</p>

---

## Part 2: Install Docker & Nginx

### Step 1: Update System Packages
```bash
sudo apt update && sudo apt upgrade -y
```
<img width="1339" height="714" alt="image" src="https://github.com/user-attachments/assets/f855f831-c2a4-45b1-824b-621bb20cfafb" />

---

## Step 2: Install Docker
```bash
sudo apt install docker.io -y
sudo systemctl status docker
```
<img width="1365" height="715" alt="image" src="https://github.com/user-attachments/assets/1926835a-55b3-43e9-802f-5dbb0614f48e" />
<img width="1348" height="368" alt="image" src="https://github.com/user-attachments/assets/df558ecd-5372-4b22-9a12-d2f9ad5ed58e" />

**If Docker is not running:**
```bash
sudo systemctl start docker
sudo systemctl enable docker
```
**And:**
Verify Docker installation:
```bash
docker --version
```
<img width="1347" height="75" alt="image" src="https://github.com/user-attachments/assets/3db6bbaf-727d-46ad-9702-298ae9457f3f" />


---

### Step 3: Install Nginx
```bash
sudo apt install nginx -y
```
<img width="1285" height="666" alt="image" src="https://github.com/user-attachments/assets/56d007d0-1d01-47fd-ae95-33debc5fe0f7" />

---

### Step 4: Verify Nginx Service
```bash
systemctl status nginx
```
<img width="1330" height="265" alt="image" src="https://github.com/user-attachments/assets/59f00170-b9bf-4b33-a22a-e9fe71acdd09" />

**If Nginx is not running:**
```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

## Part 3: Security Group Configuration

- Opened Port 80 (HTTP) in the cloud firewall / security group
- Allowed inbound traffic from 0.0.0.0/0
<img width="1154" height="231" alt="image" src="https://github.com/user-attachments/assets/094a3571-bd66-41b7-98a2-a8a2f36ac66d" />

**Test Web Access**
Opened a browser and visited:
```cpp
http://34.228.19.69
```

### Nginx Welcome Page
<img width="1365" height="768" alt="image" src="https://github.com/user-attachments/assets/fb02e788-ca4b-43b7-b5f5-eaf9e9d90668" />


<p align="center">
  <b>Figure:</b> Nginx default welcome page accessible from the internet
</p>

---

## Part 4: Extract Nginx Logs

### Step 1: View Nginx Access Logs
```bash
sudo cat /var/log/nginx/access.log
```
<img width="1366" height="609" alt="image" src="https://github.com/user-attachments/assets/cdc3bbb4-b487-4db4-82bf-82d19debb0d0" />

---

### Step 2: Save Logs to a File
```bash
sudo cat /var/log/nginx/access.log > ~/nginx-logs.txt
```


**Verify:**
```bash
ls -l nginx-logs.txt
```

### Nginx Logs File
<img width="1347" height="54" alt="image" src="https://github.com/user-attachments/assets/3cf36179-afbd-4ae5-ae46-37507623a2a8" />

<p align="center">
  <b>Figure:</b> Nginx access logs extracted and saved to file
</p>

---

**Step 3: Download Logs to Local Machine**
```local
scp -i my-key.pem ubuntu@<instance-ip>:~/nginx-logs.txt .
```
<img width="1340" height="143" alt="image" src="https://github.com/user-attachments/assets/33e4950a-1ac2-4d27-9585-e74ceae46f24" />
<img width="984" height="634" alt="image" src="https://github.com/user-attachments/assets/8426e922-e9e9-43ab-b39b-d1bc75d37835" />
<p align="center">
  <b>Figure:</b> nginx-logs.txt file downloaded successfully into local machine
</p>
---

## Challenges Faced:
- Nginx page not loading initially
- Issue was due to Port 80 not opened in security group
- Fixed by updating inbound rules and reloading the page

---

## What I Learned:
- How to launch and access a cloud server using SSH
- Installing and managing services using systemctl
- Importance of security groups and firewall rules
- How to locate and extract Nginx logs
- Real-world cloud deployment workflow

---

## My Learnings:
Deployed my first cloud-based web server using Nginx, verified public access, and extracted logs for analysis.
This felt like real production work, not just theory.
