---
Title: "Worklog Week 11"
Date: 2026-01-01
Weight: 2
Chapter: False
Pre: "<b>1.11.</b>"
---

### Week 11 Goals:
* Ensure the stability of the deployed application and thoroughly test the public frontend demo link.
* Monitor and verify the seamless connection flow between the frontend, backend, database, and storage as a complete system.
* Support the migration of product resource storage from local EC2 drives to Amazon S3 (using IAM Role).
* Perform debugging and end-to-end (E2E) testing for authentication errors, admin privileges, product file loading/preview, and S3 access permissions.

### Tasks to be implemented this week:
| Day | Task | Start Date | Completion Date | Source of Documentation |
| --- | --- | --- | --- | --- |
| 2 | - Support testing of React/Vite demo links on Vercel; review and report SPA routing errors (route `/login`, `/products`).<br>- Verify Vercel rewrites configuration: ensure `/api/*` and `/webhook/*` requests point correctly to the EC2 backend without mixed content errors. | 29/06/2026 | 29/06/2026 | https://vercel.com/docs/rewrites |
| 3 | - Check the frontend bundle on production to ensure no APIs are mistakenly calling `localhost:3000` (which has been switched to a relative path).<br>- Support verifying the permissions of IAM Roles attached to EC2, ensuring S3 permissions are strictly limited to the prefix `products/*` in the `marketplace-frontend-thao` bucket. | 30/06/2026 | June 30, 2026 | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html |
| 4 | - Test AWS CLI commands directly on EC2 to confirm that permissions to manipulate S3 (PutObject, ListBucket, DeleteObject) are working correctly.<br>- Run test scripts (QA) for file upload, stream, preview, and download flows after backend refactoring to use memoryStorage and `@aws-sdk/client-s3`. | July 1, 2026 | July 1, 2026 | https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/ |
| 5 | - Review data integrity after the team synchronized old product files from EC2 to S3.<br>- Test the functionality: thumbnail display, document preview/download, and 3D model via API.<br>- Participate in debugging and support for handling download errors on the purchase history screen (reusing the library download service). | 02/07/2026 | 02/07/2026 | https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html |
| 6 | - Test the admin-side category management UI, ensuring good support for the `DOCUMENT` and `MODEL_3D` groups.<br>- Review the architecture diagram with the team, ensuring it accurately describes the current architecture (using Vercel as frontend hosting and S3 as the storage location for product assets). | 03/07/2026 | 03/07/2026 | https://aws.amazon.com/architecture/ |

### Week 11 Results:
* Confirmed the cloud demo system (Frontend Vercel, Backend EC2, RDS PostgreSQL, S3) has successfully connected and is running smoothly.
* Tested and verified the new product upload flow: files are correctly saved to `s3://marketplace-frontend-thao/products/` instead of on the EC2 hard drive.
* The backend ownership check flow works well before streaming paid files; the S3 bucket remains secure in private mode.
* Thumbnail display, document preview/download, and 3D preview features passed tests and are stable on the S3 platform.
* System security compliance is ensured: IAM Role works effectively from EC2 without needing to store the AWS access key long-term in the `.env` file.