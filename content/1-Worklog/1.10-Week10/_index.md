---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 10 Goals:

* Ensure the stability of core functionalities (Auth, Product, Library, Purchase) before deployment.

* Support acceptance testing (UAT) on real business flows (Buyer/Admin/Seller).

* Support configuration and testing of Cloud infrastructure (EC2, RDS, S3, IAM) to ensure the system operates according to the architecture diagram.

### Tasks to be implemented this week:
| Day | Task | Start Date | Completion Date | Documentation Sources |

| --- | --- | --- | --- | --- |

| 2 | - Comprehensive review of core functionalities: Auth, product listing, search, admin dashboard. <br>- Create a list of potential errors that need to be stabilized before deploying to the cloud environment. | 22/06/2026 | 22/06/2026 | |

| 3 | - User Flow Testing: Buyer registration/login, purchase, view purchase history. <br>- Support debugging errors when loading purchase history file and 3D preview. | 23/06/2026 | 23/06/2026 | |

| 4 | - Admin/Seller Flow Testing (category, product management). <br>- Support the team in running seed-required.js securely; assign admin role via SQL to verify administrative privileges. | 24/06/2026 | 24/06/2026 | |

| 5 | - Support Backend deployment to EC2; verify private connection between EC2 and RDS PostgreSQL. <br>- Support debugging SSL errors when connecting Prisma to RDS. | 25/06/2026 | 25/06/2026 | https://docs.aws.amazon.com/rds/ |

| 6 | - Tested S3 permissions via IAM Role (least privilege). <br>- Tested the upload/stream flow of product files from S3, ensuring the backend reads data securely. | June 26, 2026 | June 26, 2026 | https://docs.aws.amazon.com/s3/ |

### Achieved Results:
* The system reached MVP status, ready for demo: Frontend runs stably on Vercel, Backend operates on EC2 with PM2.

* Data has been migrated to Amazon RDS PostgreSQL and product files are securely managed on Amazon S3 with a properly configured IAM Role.

* Supported the team to successfully fix several critical bugs: Prisma-RDS SSL error, 404 error on Vercel, issues with Admin/API Proxy permissions and S3 data synchronization.

* A soft-delete approach for products (instead of hard-delete) has been implemented to ensure order data integrity.

* Suggested next steps: Configure CloudWatch Logs, secure information with SSM Parameter Store, and optimize the frontend with CloudFront.