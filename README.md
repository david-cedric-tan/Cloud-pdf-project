<h1> Cloud-pdf-project </h1>
Cloud-Based PDF Processing Platform | AWS, Python Flask
An event-driven cloud application deployed on AWS that compares fixed-size and paragraph-aware PDF chunking strategies for document retrieval. 
Users can upload PDF files through a Flask web application, while background worker services independently process the documents and store results for side-by-side analysis.

<h3>Key Features</h3>
 Upload PDF documents through a Flask web interface
* Compare fixed-size and paragraph-aware chunking strategies
* View chunk statistics, processing times, and retrieval results
* Query processed documents using TF-IDF retrieval
* Event-driven architecture for scalable background processing

<h3>AWS Architecture</h3>

* Amazon EC2 – Hosts the Flask web application and worker services
* Application Load Balancer (ALB) – Provides public access and distributes traffic
* Auto Scaling Group (ASG) – Maintains healthy web application instances
* Amazon S3 – Stores uploaded PDF documents
* Amazon RDS (PostgreSQL) – Stores document metadata, processing status, and chunking results
* Amazon SNS – Distributes PDF upload events
* Amazon SQS – Decouples processing pipelines through dedicated queues
* Custom VPC – Implements public/private subnet architecture with Security Groups and IAM-based access controls

<h3>Workflow</h3>

1. User uploads a PDF through the web application.
2. PDF is stored in Amazon S3.
3. S3 generates an upload event.
4. SNS fans out notifications to two SQS queues.
5. Fixed-size and paragraph-aware worker processes independently consume messages.
6. Workers download the PDF, generate chunks, and store results in PostgreSQL.
7. Users compare chunking statistics and retrieval results through the web interface.

<h3>Security Features </h3>

* Private subnet deployment for application and database resources
* Security Group-based network segmentation
* IAM role-based access to AWS resources
* Bastion host for administrative access
* RDS isolated within private subnets
* S3 bucket configured with public access blocked

<h3>Technologies</h3>

Python, Flask, PostgreSQL, AWS EC2, S3, RDS, SNS, SQS, ALB, Auto Scaling Groups, IAM, Security Groups, Custom VPC
