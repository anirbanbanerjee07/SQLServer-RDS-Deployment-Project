# 🗄️ SQLServer-RDS-Deployment-Project — Frequently Asked Questions (FAQ)

---

## ❓ 1. What is this project about?
This project shows how to **deploy and manage a Microsoft SQL Server database** using **AWS RDS (Relational Database Service)**.  
It covers configuration, security, automation, and monitoring for a complete cloud-based SQL Server deployment.

---

## ⚙️ 2. What are the main components?
| Component | Description |
|------------|-------------|
| **AWS RDS (SQL Server)** | Managed relational database service |
| **EC2 / App Server** | Runs your backend application |
| **S3** | Stores automated database backups and logs |
| **CloudWatch** | Provides monitoring, alerts, and dashboards |
| **Terraform / AWS CLI** | Automates deployment and infrastructure setup |

---

## 🚀 3. How do I deploy the RDS instance?
You can use either **Terraform** or **AWS CLI scripts**.

### ✅ Option 1 — Using Terraform:
```bash
cd infrastructure/terraform
terraform init
terraform plan
terraform apply
```

### ⚙️ Option 2 — Using AWS CLI Script:
```
bash infrastructure/scripts/create_rds_instance.sh
```
---

### 🔗 4. How do I connect to the RDS SQL Server?
1. Open SQL Server Management Studio (SSMS)
2. Enter your credentials:
   ```pgsql
       Server Name: <your-rds-endpoint>
       Authentication: SQL Server Authentication
       Username: <master username>
       Password: <password>
   ```
3. Test your connection with:
    ```sql
       SELECT @@VERSION;
    ```
### 💾 5. How are backups handled?
- Automated backups are enabled within RDS.
- Manual backups can be triggered with:
  ```bash
      bash infrastructure/scripts/backup_rds_snapshot.sh
  ```
- Snapshots and logs are stored in Amazon S3.
- Backup retention is configurable in the RDS settings.

---

### 🔒 6. How is security ensured?
* **This project follows AWS security best practices:**
* Database runs in a private subnet (VPC)
* Security Groups restrict inbound traffic (port `1433` for SQL Server)
* IAM roles provide access to S3 and CloudWatch
* SSL connections ensure encrypted data transfer
* No public access to RDS in production environments

---

### 📊 7. How do I monitor RDS performance?
* **Use Amazon CloudWatch for:**
    - CPU utilization
    - Active connections
    - Free storage space
    - Read/Write IOPS
      ```bash
         monitoring/cloudwatch_dashboard.json
         monitoring/alert_rules.md
      ```

---

### 🏗️ 8. Where can I see the architecture?
📁 [docs/architecture-diagram.png]
