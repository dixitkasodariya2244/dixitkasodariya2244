
# Social Media Platform - AWS Implementation

## Table of Contents

1.	Project Overview
2.	Architecture
3.	Features
4.	AWS Services Used
5.	Setup and Deployment

  	•	Prerequisites
    •	Backend Setup
    •	Frontend Setup
    •	Deploying the Application
7.	API Endpoints
8.	Security Considerations
9.	Scalability Considerations
10.	Future Enhancements
11.	Contributing
12.	License
________________________________________

## Project Overview

This project is a basic implementation of a social media platform like Facebook, built using AWS services. The platform allows users to register, log in, follow other users, create posts, like and comment on posts, and receive notifications. The goal of this project is to demonstrate the use of AWS services to build a scalable and secure web application.
Architecture

## Architecture
![image](https://github.com/user-attachments/assets/1ab068da-87be-4a33-84ad-a9a3dc5171f2)

 
### Components:
•	Frontend: React.js hosted on Amazon S3 and served through Amazon CloudFront.
•	Backend: AWS Lambda functions orchestrated via API Gateway.
•	Database: Amazon DynamoDB for storing user data, posts, and relationships.
•	Storage: Amazon S3 for storing user-uploaded media (images, videos).
•	Authentication: Amazon Cognito for user sign-up, sign-in, and authentication.
•	Notifications: Amazon SNS for sending notifications.

### Features
•	User Management: Sign-up, login, profile management using Amazon Cognito.
•	Posts: Create, edit, delete posts with text, images, or videos.
•	News Feed: View posts from users that the current user follows.
•	Interactions: Like and comment on posts.
•	Followers: Follow and unfollow other users.
•	Notifications: Receive notifications for new followers, likes, and comments.

### AWS Services Used
•	Amazon Cognito: User authentication and management.
•	Amazon S3: Storage for user-uploaded media.
•	Amazon DynamoDB: NoSQL database for storing user data, posts, and relationships.
•	AWS Lambda: Serverless functions to handle backend logic.
•	Amazon API Gateway: API management service to create and manage RESTful APIs.
•	Amazon SNS: Simple Notification Service for sending notifications.
•	Amazon CloudFront: Content delivery network (CDN) for fast and secure delivery of frontend assets.
•	AWS CloudWatch: Monitoring and logging for AWS services.

### Setup and Deployment Prerequisites
•	AWS account
•	AWS CLI configured with appropriate permissions
•	Node.js and npm installed
•	Git installed

## Backend Setup
1.	Clone the Repository:

  	    git clone https://github.com/your-username/social-media-platform.git
        cd social-media-platform

3.	Configure AWS CLI: Make sure your AWS CLI is configured with access to deploy resources.

  	    aws configure

5.	Deploy Backend Resources:
•	Use AWS CloudFormation or Terraform to deploy resources like DynamoDB tables, S3 buckets, and Cognito.
•	Example using CloudFormation:    

  	    aws cloudformation create-stack --stack-name SocialMediaApp --template-body file://infrastructure/cloudformation/template.yaml

7.	Deploy Lambda Functions:
•	Zip your Lambda function code and upload to AWS.
•	Example:

  	    zip -r lambda-function.zip backend/lambda-functions/*
        aws lambda update-function-code --function-name YourFunctionName --zip-file fileb://lambda-function.zip

  	                                                                Frontend Setup
1.	Navigate to the Frontend Directory:

        cd frontend

3.	Install Dependencies:

  	    npm install

5.	Configure Environment Variables:
•	Create a .env file with your AWS service details (e.g., Cognito pool IDs, API Gateway URLs).
•	Example:

  	    REACT_APP_COGNITO_USER_POOL_ID=your-cognito-pool-id
        REACT_APP_API_BASE_URL=https://your-api-gateway-url.com
7.	Build the Frontend:

  	    npm run build
9.	Deploy Frontend to S3:

  	    aws s3 sync build/ s3://your-s3-bucket-name
11.	Set Up CloudFront:
•	In the AWS Console, create a CloudFront distribution pointing to your S3 bucket.


## Deploying the Application

After deploying both the backend and frontend, your application should be live and accessible via the CloudFront URL.
API Endpoints

# User Management
•	POST /signup: Register a new user.
•	POST /login: Authenticate a user.

# Posts
•	POST /posts: Create a new post.
•	GET /posts/{id}: Get a post by ID.
•	PUT /posts/{id}: Edit a post.
•	DELETE /posts/{id}: Delete a post.

# Followers
•	POST /follow: Follow a user.
•	DELETE /unfollow: Unfollow a user.

# Interactions
•	POST /like/{postId}: Like a post.
•	POST /comment/{postId}: Comment on a post.

# News Feed
•	GET /feed: Get the news feed for the current user.

# Security Considerations
•	IAM Roles: Ensure Lambda functions have the least privilege necessary.
•	Cognito: Use Cognito User Pools to secure API Gateway endpoints.
•	Encryption: Data at rest (S3, DynamoDB) and in transit (HTTPS) should be encrypted.
•	API Gateway: Use AWS WAF to protect your APIs from common web exploits.

# Scalability Considerations
•	Auto Scaling: AWS Lambda automatically scales based on the number of incoming requests.
•	DynamoDB: Set up on-demand scaling for DynamoDB to handle variable loads.
•	CloudFront: Use CloudFront caching to reduce the load on S3 and improve the content delivery speed.

# Future Enhancements
•	Direct Messaging: Implement real-time messaging between users.
•	Advanced Search: Add functionality to search for users and posts.
•	Analytics: Integrate AWS QuickSight or another analytics service to gather insights on user activity.
•	Mobile App: Develop a mobile application using AWS Amplify and React Native.

# Contributing
Contributions are welcome! Please fork the repository and submit a pull request.
Steps to Contribute:
1.	Fork the repository.
2.	Create a new feature branch.
3.	Commit your changes.
4.	Push to your fork.
5.	Submit a pull request.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

