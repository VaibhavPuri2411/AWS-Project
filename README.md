# AWS Project


Personal Expense Tracker – AWS 

1️⃣ Requirement Analysis

Goal: Track personal income and expenses in the cloud.

Features:

Add income and expense records (amount, category, date)

View summary reports (daily, weekly, monthly)

Optional: Visualize data with charts


AWS Services to use:

S3 → Store frontend files (HTML/CSS/JS)

DynamoDB → Store expense records

API Gateway → Connect frontend to backend

AWS Lambda → Backend logic (CRUD operations)




---

2️⃣ Design Architecture

High-Level Architecture:

Frontend (HTML/CSS/JS) 
        ↓
   API Gateway → AWS Lambda → DynamoDB
        ↑
   Response to Frontend

Frontend hosted on S3 (static website)

Backend implemented as serverless functions in Lambda

Database: NoSQL DynamoDB table to store transactions



---

3️⃣ AWS Setup

Step 1: DynamoDB Table

1. Go to AWS Console → DynamoDB → Create Table


2. Table name: Expenses


3. Primary key: TransactionID (String)


4. Add optional fields: Date, Type (Income/Expense), Category, Amount, Description




---

Step 2: Lambda Functions

1. Go to AWS Lambda → Create Function → Author from Scratch


2. Function Name: AddExpense


3. Runtime: Python 


4. Code handles:

Add transaction to DynamoDB

Read transactions

Update or delete records (CRUD)



5. Assign a role with DynamoDB full access

6. Crete DeleteExpense and GetExpense Function using above steps

7. Foe GetExpenseFunction only give role as DynamoDB read only acess




---

Step 3: API Gateway

1. Go to API Gateway → Create API → HTTP API


2. Add routes:

POST /addExpense → Lambda AddExpense

GET /getExpenses → Lambda GetExpense



3. Deploy API → get endpoint URL




---

Step 4: Frontend (HTML/CSS/JS)

1. Create a simple web page to:

Input transaction (amount, category, date, type)

Submit to API Gateway endpoint

Display all transactions in a table

Optional: Render charts (Chart.js)

Frontend code is in my repo saves as main code



2. Configure CORS in API Gateway to allow frontend calls




---

Step 5: Host Frontend on S3

1. Go to S3 → Create Bucket


2. Enable Static website hosting


3. Upload frontend files (HTML, CSS, JS)


4. Set bucket policy to allow public read access


5. Open S3 bucket URL → your web app is live




---

4️⃣ Testing

Open the S3 hosted website → add transactions → verify in DynamoDB

Check API Gateway → Lambda functions process requests correctly

Verify charts and summary reports




---

6️⃣ Optional Enhancements

Authentication using AWS Cognito → user-specific expenses

Notifications → email alerts for expenses using SNS

Analytics → use AWS QuickSight for advanced visualization



---

This gives you a complete step-by-step AWS workflow for your Personal Expense Tracker.




