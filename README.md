# auroravault_info


# AuroraVault: A Secure and Efficient Photo Storage Platform - www.auroravault.com

Welcome to AuroraVault, a platform designed to help users securely store and manage their memories in the form of photos. This README outlines the services and architecture used in the application, highlighting the scalability, reliability, and performance optimization strategies employed.

##Overview

AuroraVault is a cloud-based photo storage platform designed to:
	•	Store and organize user photos securely.
	•	Provide scalable solutions for metadata storage, image uploads, and retrieval.
	•	Offer a seamless and efficient experience for both individual users and families.

Features
	•	Photo Storage: Upload, store, and retrieve photos in S3 buckets.
	•	Batch Upload: Efficiently upload up to 50 images at a time.
	•	Metadata Storage: Photo metadata is stored in DynamoDB for fast retrieval.
	•	Secure Uploads: Use of presigned URLs for uploading images directly to S3.
	•	Retry Mechanism: Robust retry mechanism for image fetching with exponential backoff.
	•	Pending Fetch Queue: Maintain a list of images pending upload or fetch.
	•	Notifications: SES-powered welcome emails upon successful user registration.
	•	Event-driven Architecture: EventBridge and SQS used for communication between services.

Architecture

The architecture is built using a serverless microservices model, which ensures scalability, cost-efficiency, and high availability. Below is a high-level overview:
	1.	User Service:
	•	Handles user verification and account management.
	•	Publishes user-related events to EventBridge.
	2.	Image Service:
	•	Image Upload: Uses presigned URLs for direct S3 uploads.
	•	Image Metadata Management: Processes metadata via SQS and stores it in DynamoDB.
	•	Image Retrieval: Fetches user photos with a caching mechanism to reduce redundant calls.
	3.	Notification Service:
	•	Sends welcome emails using AWS SES.
	•	Logs email notifications in DynamoDB for auditing.
	4.	Retry Mechanism:
	•	Ensures failed fetches are retried with exponential backoff and maintains a pending queue for incomplete fetches.

Services Used

AWS Services
	1.	Amazon S3:
	•	Stores user-uploaded photos in a structured folder hierarchy (userId/yyyy/mm/dd/).
	•	Secure uploads using presigned URLs.
	2.	AWS DynamoDB:
	•	NoSQL database for storing photo metadata (e.g., timestamps, file sizes, CloudFront URLs).
	•	Designed with a partition key (userId) and sort key (fileId) for optimized queries.
	3.	AWS Lambda:
	•	Powers serverless execution for various functionalities:
	•	Processing image metadata from SQS.
	•	Storing metadata into DynamoDB.
	•	Fetching user images.
	4.	Amazon SQS:
	•	Ensures scalability by decoupling metadata processing from the upload process.
	•	Dead Letter Queue (DLQ) for handling failed messages.
	5.	Amazon SES:
	•	Sends transactional emails, such as welcome notifications upon user registration.
	6.	Amazon EventBridge:
	•	Routes user-related events (e.g., UserVerified) to target services.
	7.	AWS CloudFront:
	•	Provides CDN support for optimized image delivery.

Frontend Tools
	1.	React Native with Expo:
	•	Cross-platform mobile application development.
	•	Enables seamless photo management on iOS and Android.
	2.	AsyncStorage:
	•	Caches user photos locally for quick access.
	•	Maintains a pending fetch list for retries.
	3.	Axios:
	•	Handles API communication for image upload and retrieval.

Future Enhancements
	•	End-to-End Encryption: Encrypting photos before upload for added security.
	•	Family Sharing: Allow family members to collaboratively manage shared albums.
	•	AI Tagging: Automatically tag photos with events, locations, and people.
	•	Global Reach: Multi-region S3 buckets and DynamoDB Global Tables for reduced latency.

Contact

For inquiries, reach out at shuklavishwam111@gmail.com
