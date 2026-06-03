# AWS Serverless Library Inventory System

## Project Overview
This project demonstrates a serverless AWS solution for a library inventory management system. Library branch inventory files are uploaded as CSV files, processed automatically, stored in DynamoDB, and monitored for out-of-stock books. When a book count reaches zero, the system sends an email notification using Amazon SNS.

## Architecture
The architecture follows an event-driven serverless design:
- CSV inventory files are uploaded to Amazon S3
- S3 sends object creation events to SQS
- SQS triggers a Lambda function
- Lambda processes CSV data and stores records in DynamoDB
- DynamoDB Streams trigger another Lambda function
- Lambda checks stock count and publishes alerts through SNS
- API Gateway and Lambda retrieve data from DynamoDB
- A static webpage hosted on S3 displays inventory data

## AWS Services Used
- Amazon S3
- Amazon SQS
- AWS Lambda
- Amazon DynamoDB
- DynamoDB Streams
- Amazon SNS
- Amazon API Gateway
- CloudWatch Logs

## Key Features
- Serverless event-driven architecture
- Loosely coupled design using SQS
- Automated CSV ingestion
- Inventory data storage using DynamoDB
- Out-of-stock email notifications using SNS
- API endpoint for retrieving inventory data
- Static frontend hosted on Amazon S3

## Workflow
1. User uploads branch-specific CSV files to S3.
2. S3 event notification sends messages to SQS.
3. SQS triggers a Lambda function.
4. Lambda reads the CSV files and inserts inventory records into DynamoDB.
5. DynamoDB Stream triggers another Lambda function.
6. The second Lambda checks whether any book count is zero.
7. If stock is zero, SNS sends an email notification.
8. API Gateway triggers another Lambda function to fetch data from DynamoDB.
9. The S3-hosted static webpage displays the inventory.

## Report
The full project report is available here:

[View Full Project Report](Cloud%20Architecture%20Assignment%202%20(Report).pdf)

## Skills Demonstrated
- Serverless architecture design
- Event-driven processing
- AWS Lambda development
- DynamoDB data handling
- Queue-based decoupling with SQS
- Notification system using SNS
- API Gateway integration
- Cloud monitoring and troubleshooting

## Lessons Learned
This project helped me understand how serverless AWS services can be combined to build scalable, cost-efficient, and loosely coupled cloud applications.
