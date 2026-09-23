# 🚀 Web Hosting with GitHub Actions & AWS EC2

This project demonstrates how to **host a simple website on an AWS EC2 instance using GitHub Actions and a self-hosted GitHub Actions runner**.

The workflow automates the process of deploying website files from a GitHub repository to an AWS EC2 server whenever changes are pushed to the repository.

## 📌 Project Overview

The project demonstrates a basic **CI/CD workflow** using:

* 🐙 **GitHub** – Source code repository
* ⚙️ **GitHub Actions** – Automation and deployment
* 🖥️ **GitHub Actions Local/Self-Hosted Runner** – Executes workflow jobs locally/on the configured machine
* ☁️ **AWS EC2** – Server used for hosting the website
* 🌐 **HTML/CSS** – Simple website

## 🌐 Live Demo

The website is deployed on an AWS EC2 Ubuntu instance using
GitHub Actions, a self-hosted runner, and Nginx.

🔗 [GitHub to AWS EC2 Deployment](http://98.130.15.198/) 

## ⚠️ Instance Status

**Instance State:** `Stopped`

> The AWS EC2 instance is currently stopped.
> Please contact the owner to request access to the website or required resources.


### Architecture

```text
Developer
    │
    │ git push
    ▼
GitHub Repository
    │
    │ GitHub Actions
    ▼
Self-Hosted / Local Runner
    │
    │ Deployment
    ▼
AWS EC2 Instance
    │
    │ Web Server
    ▼
🌐 Hosted Website
```

## 🎯 Objectives

The main objectives of this project are:

1. Understand **GitHub Actions** workflows.
2. Configure and use a **self-hosted GitHub Actions runner**.
3. Connect GitHub Actions with an **AWS EC2 instance**.
4. Automate website deployment.
5. Understand the basic concept of **CI/CD**.
6. Host a simple static website on AWS.

## 🛠️ Technologies Used

| Technology         | Purpose                      |
| ------------------ | ---------------------------- |
| GitHub             | Source code management       |
| GitHub Actions     | CI/CD automation             |
| Self-Hosted Runner | Executes GitHub Actions jobs |
| AWS EC2            | Web hosting server           |
| HTML               | Website structure            |
| CSS                | Website styling              |
| Linux              | EC2 operating system         |

## 📂 Project Structure

```text
GITHUB_ACTIONS/
│
├── .github/
│   └── workflows/
│       └── deploy.yml
│
├── index.html
│
└── README.md
```

## ⚙️ How It Works

### 1. Create the Website

A simple HTML website is created and stored in the GitHub repository.

```html
<!DOCTYPE html>
<html>
<head>
    <title>AWS EC2 Hosting</title>
</head>
<body>

    <h1>Welcome to My AWS Hosted Website</h1>
    <p>This website is deployed using GitHub Actions.</p>

</body>
</html>
```

### 2. Push Code to GitHub

The website files are pushed to the GitHub repository.

```bash
git add .
git commit -m "Add website"
git push origin main
```

### 3. GitHub Actions

A GitHub Actions workflow is triggered when changes are pushed to the repository.

Example:

```yaml
name: Deploy Website

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: self-hosted

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Deploy Website
        run: |
          echo "Deploying website..."
          # Deployment commands
```

### 4. Self-Hosted Runner

The GitHub Actions job is executed using a **self-hosted runner** configured for the repository.

The runner receives the workflow instructions from GitHub and executes the required commands.

### 5. AWS EC2

An AWS EC2 instance is used as the hosting server.

The EC2 instance runs a web server such as **Apache or Nginx**, which serves the website files.

Example:

```bash
sudo apt update
sudo apt install nginx -y
```

The website can then be placed in the web server's directory.

For Nginx:

```bash
/var/www/html/
```

### 6. Website Deployment

After the GitHub Actions workflow runs successfully, the website files are deployed to the EC2 instance.

The website can then be accessed using the EC2 instance's public IP address.

```text
http://<EC2-PUBLIC-IP>
```

## 🔄 CI/CD Workflow

The overall deployment process is:

```text
Code Change
     ↓
Git Push
     ↓
GitHub Repository
     ↓
GitHub Actions Triggered
     ↓
Self-Hosted Runner
     ↓
Deploy Files
     ↓
AWS EC2
     ↓
Web Server
     ↓
🌐 Website Live
```

## 🔐 AWS EC2 Security Group

For the website to be accessible from the internet, the EC2 Security Group should allow HTTP traffic.

Example inbound rules:

| Type | Port | Source    |
| ---- | ---: | --------- |
| SSH  |   22 | Your IP   |
| HTTP |   80 | 0.0.0.0/0 |

> **Security Note:** Avoid opening SSH (port 22) to `0.0.0.0/0` unless necessary. Restrict it to your own IP whenever possible.

## 📸 Project Demonstration

The project demonstrates:

* GitHub repository
* GitHub Actions workflow
* Self-hosted/local runner
* AWS EC2 instance
* Web server configuration
* Automated website deployment
* Live website hosted on AWS

## 💡 Key Learning Outcomes

Through this project, I learned:

* How GitHub Actions workflows operate.
* How to configure a self-hosted runner.
* How to deploy files using automation.
* Basics of AWS EC2 web hosting.
* Linux server administration.
* Basic CI/CD concepts.
* How source-code changes can trigger automated deployment.

## 🚀 Future Improvements

This project can be extended by adding:

* Docker-based deployment
* Nginx reverse proxy
* HTTPS using Let's Encrypt
* Custom domain
* AWS IAM roles
* Automated rollback
* Docker Hub integration
* Kubernetes deployment
* Infrastructure as Code using Terraform

## 👨‍💻 Author

**Krushna**

GitHub: [Oaklaan](https://github.com/Oaklaan)

---

⭐ If you found this project useful, consider giving the repository a star!
