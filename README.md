# 🚀 AWS Systems Manager Lab – Centralized EC2 Management Without SSH

![AWS](https://img.shields.io/badge/AWS-Systems%20Manager-orange)
![EC2](https://img.shields.io/badge/Amazon-EC2-yellow)
![Session Manager](https://img.shields.io/badge/Session-Manager-blue)
![Parameter Store](https://img.shields.io/badge/Parameter-Store-green)
![Automation](https://img.shields.io/badge/Infrastructure-Automation-red)

## 📖 Project Overview

This project demonstrates how to manage Amazon EC2 instances securely and centrally using AWS Systems Manager without relying on traditional SSH access.

The lab explores several Systems Manager capabilities including inventory collection, remote command execution, configuration management, and secure browser-based access to Linux instances.

This approach reflects modern operational practices used in Cloud Computing and DevOps environments.

---

# 🎯 Objectives

* Manage EC2 instances centrally
* Collect inventory information automatically
* Execute commands remotely using Run Command
* Store application configurations using Parameter Store
* Access EC2 instances securely with Session Manager
* Eliminate SSH dependency
* Improve operational security and scalability

---

# 🏗 Solution Architecture

```text
                          Administrator
                                 │
                                 ▼
                    AWS Systems Manager
                                 │
        ┌──────────────┬───────────────┬───────────────┐
        │              │               │
        ▼              ▼               ▼
  Fleet Manager    Run Command    Parameter Store
        │              │               │
        └──────────────┴───────────────┘
                         │
                         ▼
                 Managed EC2 Instance
                         │
                         ▼
                  Session Manager
                         │
                         ▼
                    Linux Shell
```

---

# ⚙️ AWS Services Used

| Service             | Purpose                               |
| ------------------- | ------------------------------------- |
| AWS Systems Manager | Centralized infrastructure management |
| Amazon EC2          | Managed server                        |
| Fleet Manager       | Inventory and server management       |
| Run Command         | Remote command execution              |
| Parameter Store     | Configuration management              |
| Session Manager     | Secure access without SSH             |
| IAM                 | Permissions and access control        |
| AWS CLI             | Administrative commands               |

---

# 🛠 Implementation Steps

---

# Step 1 - Configure Inventory Using Fleet Manager

Fleet Manager was configured to collect information from the managed EC2 instance.

### Configuration

| Parameter        | Value                 |
| ---------------- | --------------------- |
| Association Name | Inventory-Association |
| Target           | Managed Instance      |

### Information Collected

* Installed applications
* Operating system details
* Packages
* System metadata
* Configuration information

### Result

Inventory data became available without requiring SSH access.

---

# Step 2 - Deploy Application Using Run Command

Run Command was used to install and configure a web application remotely.

### Document Executed

```text
Install Dashboard App
```

### Tasks Performed

* Install Apache Web Server
* Install PHP
* Install AWS SDK
* Deploy Widget Manufacturing Dashboard

### Result

The application was installed automatically and became accessible through a browser.

---

# Step 3 - Manage Configuration with Parameter Store

A parameter was created to enable beta features in the application.

### Configuration

| Parameter | Value                         |
| --------- | ----------------------------- |
| Name      | /dashboard/show-beta-features |
| Type      | String                        |
| Value     | True                          |

### Purpose

The application dynamically retrieved this parameter to enable additional dashboard functionality.

### Benefits

* Centralized configuration
* No application code changes required
* Improved maintainability

---

# Step 4 - Access EC2 Without SSH Using Session Manager

Session Manager provided browser-based access to the Linux instance.

### Commands Executed

List application files:

```bash
ls /var/www/html
```

Retrieve Availability Zone:

```bash
AZ=`curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone`
export AWS_DEFAULT_REGION=${AZ::-1}
```

Describe EC2 instances:

```bash
aws ec2 describe-instances
```

### Result

Secure shell access was achieved without:

* SSH keys
* Port 22 exposure
* Bastion hosts

---

# 🔐 Security Benefits

* No inbound SSH ports required
* Reduced attack surface
* Centralized access management
* IAM-based authentication
* CloudTrail auditing support

---

# 📚 Concepts Demonstrated

| Concept          | Description                           |
| ---------------- | ------------------------------------- |
| Systems Manager  | Centralized infrastructure management |
| Fleet Manager    | Inventory and server administration   |
| Run Command      | Remote execution                      |
| Parameter Store  | Configuration storage                 |
| Session Manager  | Browser-based access                  |
| Managed Instance | SSM-enabled EC2                       |
| SSM Agent        | Communication agent                   |
| IAM              | Permissions and authentication        |

---

# 📊 Benefits of AWS Systems Manager

✅ Improved security

✅ Elimination of SSH access

✅ Centralized administration

✅ Operational automation

✅ Scalable management

✅ Auditability with CloudTrail

✅ Reduced operational complexity

---

# 🎓 Learning Outcomes

This project provided hands-on experience with:

* Infrastructure automation
* Server administration without SSH
* Configuration management
* Remote command execution
* AWS CLI operations
* Secure access to EC2 instances
* Centralized infrastructure management

---

# 📂 Repository Structure

```text
aws-systems-manager-lab
│
├── README.md
├── images
│     ├── architecture.png
│     ├── fleet-manager.png
│     ├── run-command.png
│     ├── parameter-store.png
│     ├── session-manager.png
│     └── dashboard-app.png
│
├── scripts
│     ├── install-dashboard.sh
│     └── aws-cli-commands.sh
│
└── docs
      └── lab-notes.md
```

---

# 📚 Skills Demonstrated

* AWS Systems Manager
* Fleet Manager
* Session Manager
* Run Command
* Parameter Store
* Linux Administration
* AWS CLI
* IAM
* Infrastructure Automation
* Cloud Operations
* DevOps Fundamentals

---

# 📌 Author

**Paulo Henrique

AWS Cloud Practitioner Candidate | Cloud Computing Enthusiast

---

## ⭐ If you found this project useful, feel free to star the repository.
