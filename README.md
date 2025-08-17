## AWS S3 Security Lab

Implemented, tested and documented S3 bucket security configurations and public access detection in AWS. Covered creation, policy and encryption management, public access simulation and misconfiguration detection using AWS Trusted Advisor.

---

## Table of Contents

- [Overview](#overview)
- [Real-World Risk](#real-world-risk)
- [What I Built](#what-i-built)
- [Diagram](#diagram)
- [Objectives](#objectives)
- [Steps Performed](#steps-performed)
  - [1. S3 Bucket Creation]
  - [2. Bucket Policy Configuration]
  - [3. Bucket Encryption Configuration]
  - [4. Access Control Verification]
  - [5. Public Access Test]
  - [6. Misconfiguration Detection]
  - [7. Cleanup]
- [Screenshots](#screenshots)
- [Lessons Learned](#lessons-learned)
- [References](#references)
- [Contact](#contact)

---

## Overview

This lab focused on the security lifecycle for Amazon S3 buckets. The workflow included creating both private and intentionally public buckets, applying best-practice access policies, configuring server-side encryption, simulating a misconfiguration, and detecting issues using AWS Trusted Advisor. The steps demonstrate practical skills essential for AWS cloud security roles.

---

## Real-World Risk

Misconfigured Amazon S3 buckets are one of the most common causes of large-scale data breaches in the cloud. Publicly accessible buckets can unintentionally expose sensitive data—including personal information, intellectual property or critical business documents—to the entire internet. Attackers often scan for such misconfigurations and can quickly exploit them, leading to compliance violations, reputation damage and significant financial loss. Proactively securing S3 buckets and continuously monitoring for public access is essential for any organization operating in the cloud.

---

## What I Built

- Created both secure (private) and intentionally misconfigured (public) S3 buckets for demonstration purposes.
- Applied JSON bucket policies to enforce or allow access as required.
- Enabled server-side encryption using SSE-S3 and SSE-KMS.
- Uploaded and tested public file access via incognito browser.
- Attempted detection of public access misconfiguration using AWS Trusted Advisor and documented results.
- Included comprehensive screenshots, sample policy JSONs and a clear architecture diagram.

---

## Diagram

![Lab Architecture Diagram](diagram.png)

---

## Objectives

- Create secure and intentionally misconfigured (public) S3 buckets.
- Apply JSON bucket policies for granular access control.
- Enable and test server-side encryption (SSE-S3, SSE-KMS).
- Simulate and verify public access to S3 objects.
- Detect misconfiguration with AWS Trusted Advisor (noting account limitations).

---

## Steps Performed

**1. S3 Bucket Creation**
   - Created two S3 buckets: one private (sebastiansilva-private-bucket) and one intentionally public (sebastiansilva-public-bucket)
   - Verified both buckets were created in the AWS S3 Console *(Screenshot: `s3-bucket-list.png`)*

**2. Bucket Policy Configuration**
   - Applied a policy to the private bucket to enforce secure access (HTTPS-only. *Screenshot: `private-bucket-policy.png`)*
   - Applied a public-read policy to the public bucket to simulate real-world misconfiguration *(Screenshot: `public-bucket-policy.png`)*

**3. Bucket Encryption Configuration**
   - Enabled SSE-S3 (Amazon-managed keys) on the private bucket *(Screenshot: `private-bucket-encryption.png`)*
   - Enabled SSE-KMS (KMS-managed keys) on the public bucket *(Screenshot: `public-bucket-encryption.png`)*

**4. Access Control Verification**
   - Confirmed Block Public Access was ON for the private bucket and OFF for the public bucket *(Screenshots: `private-bucket-permissions.png` & `public-bucket-permissions.png`)*

**5. Public Access Test**
   - Uploaded a test file (hello.txt) to the public bucket.
   - Accessed the file from an incognito browser to verify public exposure *(Screenshot: `public-bucket-file-public-access.png`)*

**6. Misconfiguration Detection**
   - Attempted to detect the public bucket via AWS Trusted Advisor.
   - Documented results and noted Free Tier limitations *(Screenshot: `trusted-advisor-no-s3-check.png`)*

**7. Cleanup**
   - Deleted all S3 buckets and uploaded objects.
   - Scheduled deletion for any KMS keys created.
   - Verified no lingering AWS resources to avoid ongoing charges.
   
---

## Screenshots

*All screenshots are included in the `screenshots/` folder of this repository.*

| Order | File Name                            | What it Shows                                       |
|-------|--------------------------------------|-----------------------------------------------------|
| 1     | s3-bucket-list.png                   | List of S3 buckets: private and public buckets      |
| 2     | private-bucket-policy.png            | Private bucket policy requiring HTTPS               |
| 3     | public-bucket-policy.png             | Public bucket policy allowing public read access    |
| 4     | private-bucket-encryption.png        | SSE-S3 encryption enabled on private bucket         |
| 5     | public-bucket-encryption.png         | SSE-KMS encryption enabled on public bucket         |
| 6     | private-bucket-permissions.png       | Block Public Access ON for private bucket           |
| 7     | public-bucket-permissions.png        | Block Public Access OFF for public bucket           |
| 8     | public-bucket-file-public-access.png | Successful public file access from incognito browser|
| 9     | trusted-advisor-no-s3-check.png      | Trusted Advisor showing no S3 checks (Free Tier)    |

---

## Lessons Learned

- S3 bucket misconfigurations are a common source of cloud data breaches.
- AWS provides robust tools for securing and monitoring S3, but proper policy and encryption configuration is critical.
- Public access risks should be detected both automatically (e.g., Trusted Advisor) and manually.
- Understanding AWS Free Tier limitations is important for documentation and real-world troubleshooting.

---

## References

- [AWS S3 Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
- [AWS S3 Bucket Policies](https://docs.aws.amazon.com/AmazonS3/latest/userguide/example-bucket-policies.html)
- [AWS S3 Encryption](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingServerSideEncryption.html)
- [AWS Trusted Advisor](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html)

*Note:* Some AWS-managed or service-linked roles cannot be deleted manually and are retained by AWS for service management. Full Trusted Advisor checks (including S3 public bucket detection) require a Business or Enterprise support plan. For this lab, public access was validated manually.

---

## Contact

Sebastian Silva C. – July, 2025 – Berlin, Germany.  
[LinkedIn](https://www.linkedin.com/in/sebastiansilc) | [GitHub](https://github.com/SebaSilC) | [sebastian@playbookvisualarts.com](mailto:sebastian@playbookvisualarts.com)
