# GCP NGINX Web Server Deployment with Firewall Rules

## Project Overview

This project demonstrates how to deploy an **NGINX web server on a Google Cloud Compute Engine VM** and configure **VPC firewall rules** to allow HTTP traffic from the internet.

The web server runs on an **Ubuntu Linux VM**, and users can access it using the VM's **external IP address**.

This project demonstrates basic **cloud networking, firewall configuration, and Linux server administration** in Google Cloud Platform.

---

## Architecture

![Architecture Diagram](architecture-diagram.png)

### Architecture Flow

Internet User → Firewall Rule (Allow TCP:80) → Compute Engine VM → NGINX Web Server

---

## Services Used

* Google Cloud Compute Engine
* VPC Network
* Firewall Rules
* Ubuntu Linux
* NGINX Web Server
* SSH

---

## Project Structure

```
gcp-nginx-firewall-webserver
│
├── README.md
├── architecture-diagram.png
│
└── screenshots
    ├── curl-test.png
    ├── firewall-rule-created.png
    ├── nginx-browser-output.png
    ├── nginx-running.png
    ├── ssh-nginx-install.png
    └── vm-instance-created.png
```

---

## Implementation Steps

### 1. Create a VM Instance

A Compute Engine virtual machine was created with the following configuration:

Name: nginx-server
Machine type: e2-micro
Region: us-central1
Boot disk: Ubuntu Linux
External IP: Enabled

Screenshot:

![VM Instance](screenshots/vm-instance-created.png)

---

### 2. Create Firewall Rule

A firewall rule was created to allow HTTP traffic from the internet.

Configuration:

Direction: Ingress
Source IP Range: 0.0.0.0/0
Protocol: TCP
Port: 80

Screenshot:

![Firewall Rule](screenshots/firewall-rule-created.png)

---

### 3. Connect to the VM Using SSH

The VM instance was accessed using the **Google Cloud Console SSH terminal**.

Screenshot:

![SSH Terminal](screenshots/ssh-nginx-install.png)

---

### 4. Install NGINX

NGINX was installed using the apt package manager.

Commands used:

```
sudo apt update
sudo apt install nginx -y
```

Screenshot:

![NGINX Install](screenshots/ssh-nginx-install.png)

---

### 5. Start and Verify NGINX

The NGINX service was started and verified.

```
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
```

Screenshot:

![NGINX Running](screenshots/nginx-running.png)

---

### 6. Test the Web Server

The server was tested locally inside the VM using curl.

```
curl localhost
```

Screenshot:

![Curl Test](screenshots/curl-test.png)

---

### 7. Access the Website from Browser

The NGINX web server was accessed from a browser using the VM's **external IP address**.

Example:

```
http://EXTERNAL-IP
```

The default **NGINX welcome page** appeared successfully.

Screenshot:

![NGINX Browser Output](screenshots/nginx-browser-output.png)

---

## Troubleshooting

### Issue

The NGINX page was not accessible initially.

### Cause

HTTP traffic was blocked because the firewall rule allowing port 80 had not been configured.

### Solution

Created a firewall rule allowing:

Protocol: TCP
Port: 80
Source: 0.0.0.0/0

After applying the firewall rule, the web server became accessible.

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

* Google Cloud Compute Engine
* VPC Networking
* Firewall Configuration
* Linux Server Administration
* Web Server Deployment
* Cloud Troubleshooting

---

## Future Improvements

* Deploy multiple NGINX servers
* Configure HTTP Load Balancer
* Containerize NGINX using Docker
* Deploy using Kubernetes
* Automate infrastructure using Terraform

---

## Author

Sravan A L
B.Tech CSE (IoT)
Manipal University Jaipur
Aspiring Cloud / DevOps Engineer
