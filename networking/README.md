# AWS EC2 Web Server & DNS Routing

## 🚀 What I Built
I deployed a live NGINX web server on an AWS EC2 instance and successfully routed public internet traffic to it using a custom domain.

To demonstrate cloud-native resource management and cost optimization, I engineered this project to have zero overhead costs. I utilized the AWS Free Tier for compute resources and configured a dynamic DNS provider (FreeDNS) to handle the custom domain and 'A' Record routing.

## 🛠️ Architecture & Tech Stack
*   **Cloud Provider:** AWS (Elastic Compute Cloud - EC2)
*   **OS:** Linux
*   **Web Server:** NGINX
*   **Networking / DNS:** FreeDNS (A Record routing), AWS Security Groups (Virtual Firewalls)

## 🧠 What I Learnt
Completing this project solidified my understanding of foundational cloud networking concepts:
*   **Provisioning Infrastructure:** Launching and connecting to a Linux virtual machine in the cloud via SSH.
*   **Port Management:** Configuring AWS Security Groups to explicitly allow inbound SSH (Port 22) for remote management and HTTP (Port 80) for web traffic.
*   **DNS Resolution:** Understanding how the Domain Name System works in practice by mapping an 'A' Record from a custom subdomain directly to an EC2 Public IPv4 address.
*   **Linux Service Management:** Using `systemctl` to start, enable, and verify the status of background web services.

## 💻 Commands Used
Here is the sequence of commands used to update the server, install NGINX, and ensure the service starts automatically on boot:

```bash
# Update package lists
sudo yum update -y   # (or apt update for Ubuntu)

# Install NGINX
sudo yum install -y nginx

# Enable NGINX to start on boot
sudo systemctl enable nginx

# Start the NGINX service
sudo systemctl start nginx

# Verify the service is running correctly
sudo systemctl status nginx

🚧 Challenges & Solutions
The HTTPS Timeout Trap: Initially, the web page appeared to hang indefinitely. I realized modern browsers default to forcing a secure https:// connection (Port 443). Since the server was only configured for HTTP, I solved this by explicitly typing http:// in the address bar to connect via Port 80.

Firewall Configuration: I learned firsthand that installing a web server is only half the battle. If the AWS Security Group does not have an inbound rule allowing TCP traffic on Port 80 from 0.0.0.0/0, the server will silently drop all web requests.
```

📸 Proof of Deployment

![NGINX Landing Page](./aws-ec2-web-server.jpeg)
