# GCP NGINX Web Server Deployment with Firewall Rules

## Project Overview

This project demonstrates how to deploy an **NGINX web server on a Google Cloud Compute Engine virtual machine** and configure **VPC firewall rules** to allow HTTP traffic from the internet.

A virtual machine running **Ubuntu Linux** hosts the NGINX server, and users can access the website through the VM’s **external IP address**.

This project demonstrates basic **cloud networking, firewall configuration, and Linux server administration** using Google Cloud Platform.

---

## Architecture

Internet User  
↓  
Firewall Rule (Allow TCP Port 80)  
↓  
Compute Engine Virtual Machine  
↓  
NGINX Web Server  

---

## Services Used

- Google Cloud Compute Engine
- VPC Network
- Firewall Rules
- Ubuntu Linux
- NGINX Web Server
- SSH

---

## Implementation Steps

### 1. Create a Virtual Machine

A Compute Engine virtual machine was created with the following configuration:

Name: nginx-server  
Machine type: e2-micro  
Region: us-central1  
Boot disk: Ubuntu Linux  
External IP: Enabled  

This VM hosts the NGINX web server.

---

### 2. Create a Firewall Rule

A firewall rule was created to allow HTTP traffic from the internet.

Configuration:

Direction: Ingress  
Source IP Range: 0.0.0.0/0  
Protocol: TCP  
Port: 80  

This allows users on the internet to access the web server running on the VM.

---

### 3. Connect to the VM Using SSH

The virtual machine was accessed using SSH from the Google Cloud Console.

SSH allows secure remote access to the Linux server for installation and configuration.

---

### 4. Install NGINX

NGINX was installed using the Ubuntu package manager.

Commands used:

```
sudo apt update
sudo apt install nginx -y
```

---

### 5. Start and Enable NGINX

The NGINX service was started and configured to run automatically when the VM boots.

```
sudo systemctl start nginx
sudo systemctl enable nginx
```

To verify the service status:

```
sudo systemctl status nginx
```

---

### 6. Test the Web Server Locally

The web server was tested inside the virtual machine using curl.

```
curl localhost
```

If NGINX is running correctly, the command returns the default NGINX HTML page.

---

### 7. Access the Website from a Browser

The website can be accessed by entering the VM’s external IP address in a browser.

Example:

```
http://EXTERNAL-IP
```

The NGINX welcome page confirms that the web server is successfully deployed.

---

## Troubleshooting

### Issue

The NGINX page may not be accessible from the browser.

### Cause

HTTP traffic may be blocked because no firewall rule allows port 80.

### Solution

Create a firewall rule allowing incoming HTTP traffic.

Configuration:

Protocol: TCP  
Port: 80  
Source Range: 0.0.0.0/0  

After applying the firewall rule, the NGINX web server becomes accessible.

---

## Commands Used

```
sudo apt update
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
curl localhost
```

---

## Skills Demonstrated

- Google Cloud Compute Engine
- VPC Networking
- Firewall Configuration
- Linux Server Administration
- Web Server Deployment
- Cloud Troubleshooting

---

## Future Improvements

- Deploy multiple NGINX servers
- Configure an HTTP Load Balancer
- Containerize NGINX using Docker
- Deploy using Kubernetes
- Automate infrastructure using Terraform

---

## Author

Sravan A L
