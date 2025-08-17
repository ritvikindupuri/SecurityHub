# AWS Serverless Security Scanning with Prowler

**by Ritvik Indupuri**

<img width="816" height="636" alt="Screenshot 2025-08-17 143927" src="https://github.com/user-attachments/assets/3c8f5c22-e8b3-4847-bfd3-5f900adfbbd0" />
*Figure 1: Architecture for Automated AWS Security Scanning with Prowler*

---

## 📌 Overview

This project showcases a **serverless AWS-based security automation system** that scans cloud infrastructure using the open-source tool **Prowler**, evaluates against **CIS Benchmarks**, and ingests results into **AWS Security Hub** for centralized monitoring. The architecture is designed for scalability, cost-efficiency, and continuous compliance visibility.

---

## 🎯 Project Goals

- Automatically scan AWS accounts for security misconfigurations.
- Map findings to CIS AWS Foundations Benchmark v1.4.
- Trigger scans on a **daily schedule** using **CloudWatch Events**.
- Export findings in `.csv`, `.html`, and `.asff.json` formats.
- Ingest alerts into **AWS Security Hub** for triage and visualization.
- Operate in a **fully serverless and automated** manner.

---

## 🧱 System Components

| Component        | Description |
|------------------|-------------|
| **AWS CodeBuild** | Runs Prowler with a custom buildspec file. |
| **Prowler**       | Performs 105+ CIS compliance checks. |
| **S3 Bucket**     | Stores reports in `.html`, `.csv`, and `.json` (ASFF). |
| **Security Hub**  | Displays findings in a centralized dashboard. |
| **CloudWatch Events** | Schedules and triggers scans daily. |
| **IAM Roles**     | Scoped permissions to follow least-privilege access. |

---

## 🧪 Results Summary

- **Total Checks Performed**: 105
- **Passes**: 59
- **Fails**: 43
  - 12 from IAM misconfigurations
  - 15 from CloudWatch logging issues
  - Others from S3, VPC, Config, and EC2
- **Security Hub Ingestion**: 43 findings automatically loaded with severity and remediation details

---

## 🔐 Example Findings

| Severity | Category    | Description                              |
|----------|-------------|------------------------------------------|
| CRITICAL | IAM         | Root user lacks MFA                      |
| HIGH     | S3          | Buckets allow public access              |
| HIGH     | CloudTrail  | Trails not integrated with CloudWatch    |
| MEDIUM   | EC2         | Security groups allow unrestricted ports |
| LOW      | Config      | AWS Config not recording all regions     |

---

## 🛠️ Technologies Used

- **AWS CloudWatch Events** – Schedule scans.
- **AWS CodeBuild** – Containerized Prowler execution.
- **AWS S3** – Store multi-format results.
- **AWS Security Hub** – View, triage, and manage alerts.
- **IAM Policies** – Secure each component individually.
- **Prowler** – Audit and scan based on best practices.
- **Python** – (Optional) for log parsing or future extensions.

---

## 📂 Output Formats

- `prowler-output.html` – For visual inspection
- `prowler-output.csv` – For analysis or dashboard ingestion
- `prowler-output.asff.json` – Native format for Security Hub

---

## 📈 Metrics & Impact

- ✅ Reduced manual compliance efforts by **90%**
- ⏱️ Scans complete in **~6 minutes per region**
- 💡 Identified and remediated **43 real misconfigurations**
- 📊 Improved CIS Benchmark compliance score to **56.19%**

---

## 💡 Future Plans

- Add Lambda to auto-remediate critical findings.
- Notify teams via Slack/Email upon scan completion.
- Extend for multi-account orgs using STS AssumeRole.
- Tag findings by AWS service owner for accountability.

---

## 🧠 Learning Outcomes

- ✅ Automated security auditing in serverless AWS
- ✅ Deep understanding of IAM, S3, CloudTrail hardening
- ✅ Experience mapping vulnerabilities to industry benchmarks
- ✅ Practical DevSecOps and alert pipeline design

---

## 👨‍💻 Author

**Ritvik Indupuri**  
Cloud Security Engineer | Focused on secure architectures, automation, and continuous compliance.


---

