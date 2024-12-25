# AuroraVault: A Secure and Efficient Photo Storage Platform
[www.auroravault.com](https://www.auroravault.com)

Welcome to **AuroraVault**, a platform designed to help users securely store and manage their memories in the form of photos. This README outlines the services and architecture used in the application, highlighting scalability, reliability, and performance optimization.

---

## Overview
AuroraVault is a cloud-based photo storage platform designed to:
- Store and organize user photos securely.
- Provide scalable solutions for metadata storage, image uploads, and retrieval.
- Offer a seamless and efficient experience for individual users and families.

---

## Features
- **Photo Storage**: Upload, store, and retrieve photos in S3 buckets.
- **Batch Upload**: Efficiently upload up to 50 images at a time.
- **Metadata Storage**: Metadata stored in DynamoDB for fast retrieval.
- **Secure Uploads**: Use of presigned URLs for uploading images directly to S3.
- **Retry Mechanism**: Robust retry mechanism for image fetching with exponential backoff.
- **Pending Fetch Queue**: Maintain a list of images pending upload or fetch.
- **Notifications**: SES-powered welcome emails upon successful user registration.

---

## Architecture (Available soon)
![WIP]()

---
## Prototype

1. ![Login]([https://drive.google.com/file/d/1LD4UAmXL6x3EeEyshHP1A8iUNs36JWu1/view?usp=sharing])
2. [Sign Up]([link-to-signup-prototype-image](https://drive.google.com/file/d/1CCiUSzX4D7MD1_fOet1i3J6vI31lE3wk/view?usp=sharing))
3. [Reset Password]([link-to-reset-password-prototype-image](https://drive.google.com/file/d/1_QY0oksTgewaDjHHWyJvhAF1yxt3-q1Q/view?usp=sharing))
4. [Home Page]([link-to-home-page-prototype-image](https://drive.google.com/file/d/1ZlB2Z5oj4Y1E01kMJCWe840VItBlYMPT/view?usp=sharing))
5. [Uploading]([link-to-home-page-prototype-image](https://drive.google.com/file/d/1_buvqC7SqtBEZiNhjrTaIV9gGV9_VdYM/view?usp=sharing))

---

## Services Used
### AWS Services
- **Amazon S3**: Photo storage with presigned URLs.
- **AWS DynamoDB**: Metadata storage with optimized partitioning.
- **AWS Lambda**: Serverless processing for metadata, uploads, and notifications.
- **Amazon SQS**: Queue for scalable metadata processing.
- **AWS SES**: Email notifications.
- **Amazon EventBridge**: Event-driven architecture.

---
## Frontend Tools
1. **React Native with Expo**
   - Cross-platform mobile application development.
   - Enables seamless photo management on iOS and Android.

2. **AsyncStorage**
   - Caches user photos locally for quick access.
   - Maintains a pending fetch list for retries.

3. **Axios**
   - Handles API communication for image upload and retrieval.

---

## Load Test

Load testing was done on 10k+ Concurrent users and the system scaled beatufically with 0% failure rate. The RPS was at 2300. I will be pushing this to 100k and later millions.

---

## Future Enhancements
- **End-to-End Encryption**: Encrypting photos before upload for added security.
- **Family Sharing**: Allow family members to collaboratively manage shared albums.
- **AI Tagging**: Automatically tag photos with events, locations, and people.
- **Global Reach**: Multi-region S3 buckets and DynamoDB Global Tables for reduced latency.

##Contact

For inquiries, reach out at shuklavishwam111@gmail.com
