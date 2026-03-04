# GCP NGINX Web Server Deployment with Firewall Rules

## Project Overview

This project demonstrates how to deploy an **NGINX web server on a Google Cloud Compute Engine VM** and configure **VPC firewall rules** to allow HTTP traffic from the internet.

A virtual machine running **Ubuntu Linux** hosts the NGINX server, and users can access the website through the VM’s **external IP address**.

This project demonstrates basic **cloud networking, firewall configuration, and Linux server administration** using Google Cloud Platform.

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
    ├── vm-instance.png
    ├── firewall-rule.png
    ├── ssh-terminal.png
    ├── nginx-status.png
    ├── curl-test.png
    └── nginx-browser.png
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

![VM Instance](screenshots/vm-instance.png)

---

### 2. Create Firewall Rule

A firewall rule was created to allow HTTP traffic from the internet.

Configuration:

Direction: Ingress
Source IP Range: 0.0.0.0/0
Protocol: TCP
Port: 80

Screenshot:

![Firewall Rule](screenshots/firewall-rule.png)

---

### 3. Connect to the VM Using SSH

The VM instance was accessed using the **Google Cloud Console SSH terminal**.

Screenshot:

![SSH Terminal](screenshots/ssh-terminal.png)

---

### 4. Install NGINX

NGINX was installed using the apt package manager.

Commands used:

```
sudo apt update
sudo apt install nginx -y
```

---

### 5. Start and Enable NGINX

The NGINX service was started and configured to run automatically when the VM starts.

```
sudo systemctl start nginx
sudo systemctl enable nginx
```

Service status was verified using:

```
sudo systemctl status nginx
```

Screenshot:

![NGINX Status](screenshots/nginx-status.png)

---

### 6. Test the Web Server Locally

The web server was tested inside the VM using curl.

```
curl localhost
```

Screenshot:

![Curl Test](screenshots/curl-test.png)

---

### 7. Access the Website via Browser

The NGINX web server was accessed from a browser using the VM’s **external IP address**.

Example:

```
http://EXTERNAL-IP
```

The NGINX welcome page was successfully displayed.

Screenshot:

![NGINX Webpage](screenshots/nginx-browser.png)

---

## Troubleshooting

### Issue

The NGINX page was not accessible initially from the browser.

### Cause

HTTP traffic was blocked because the VM was created without allowing HTTP traffic or without a firewall rule.

### Solution

A firewall rule was created allowing incoming HTTP traffic.

Configuration:

Protocol: TCP
Port: 80
Source: 0.0.0.0/0

After applying the firewall rule, the NGINX web server became accessible.

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

