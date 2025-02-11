Here’s a comprehensive list of common AWS CLI commands, categorized based on different services and tasks you might encounter in AWS. 

### **1. AWS CLI Setup and Configuration**

- **Configure AWS CLI** (sets up AWS credentials, region, and output format):
  ```bash
  aws configure
  ```

- **Check AWS CLI version**:
  ```bash
  aws --version
  ```

- **List available AWS CLI profiles**:
  ```bash
  aws configure list-profiles
  ```

### **2. EC2 (Elastic Compute Cloud)**

- **Launch an EC2 instance**:
  ```bash
  aws ec2 run-instances --image-id <AMI-ID> --count 1 --instance-type t2.micro --key-name <key-name> --security-group-ids <SG-ID> --subnet-id <subnet-id>
  ```

- **Describe EC2 instances**:
  ```bash
  aws ec2 describe-instances
  ```

- **Stop an EC2 instance**:
  ```bash
  aws ec2 stop-instances --instance-ids <instance-id>
  ```

- **Start an EC2 instance**:
  ```bash
  aws ec2 start-instances --instance-ids <instance-id>
  ```

- **Terminate an EC2 instance**:
  ```bash
  aws ec2 terminate-instances --instance-ids <instance-id>
  ```

- **Create an EC2 key pair**:
  ```bash
  aws ec2 create-key-pair --key-name <key-name>
  ```

- **Describe EC2 security groups**:
  ```bash
  aws ec2 describe-security-groups
  ```

### **3. S3 (Simple Storage Service)**

- **Create an S3 bucket**:
  ```bash
  aws s3 mb s3://<bucket-name>
  ```

- **List S3 buckets**:
  ```bash
  aws s3 ls
  ```

- **Upload a file to an S3 bucket**:
  ```bash
  aws s3 cp <file-path> s3://<bucket-name>/path/
  ```

- **Download a file from an S3 bucket**:
  ```bash
  aws s3 cp s3://<bucket-name>/path/<file-name> <local-path>
  ```

- **Sync a directory to an S3 bucket**:
  ```bash
  aws s3 sync <local-dir> s3://<bucket-name>/path/
  ```

- **Delete an S3 object**:
  ```bash
  aws s3 rm s3://<bucket-name>/path/<file-name>
  ```

- **Delete an S3 bucket** (empty bucket first):
  ```bash
  aws s3 rb s3://<bucket-name> --force
  ```

### **4. IAM (Identity and Access Management)**

- **Create an IAM user**:
  ```bash
  aws iam create-user --user-name <user-name>
  ```

- **Attach a policy to an IAM user**:
  ```bash
  aws iam attach-user-policy --user-name <user-name> --policy-arn arn:aws:iam::aws:policy/<policy-name>
  ```

- **List IAM users**:
  ```bash
  aws iam list-users
  ```

- **Create an IAM role**:
  ```bash
  aws iam create-role --role-name <role-name> --assume-role-policy-document file://<trust-policy-document>.json
  ```

- **Attach a policy to an IAM role**:
  ```bash
  aws iam attach-role-policy --role-name <role-name> --policy-arn arn:aws:iam::aws:policy/<policy-name>
  ```

- **List IAM roles**:
  ```bash
  aws iam list-roles
  ```

### **5. Lambda**

- **Create a Lambda function**:
  ```bash
  aws lambda create-function --function-name <function-name> --zip-file fileb://<deployment-package>.zip --handler <handler> --runtime <runtime> --role arn:aws:iam::<account-id>:role/<role-name>
  ```

- **Invoke a Lambda function**:
  ```bash
  aws lambda invoke --function-name <function-name> output.txt
  ```

- **List Lambda functions**:
  ```bash
  aws lambda list-functions
  ```

### **6. CloudWatch**

- **Create a CloudWatch alarm**:
  ```bash
  aws cloudwatch put-metric-alarm --alarm-name <alarm-name> --metric-name <metric-name> --namespace <namespace> --statistic <statistic> --period <period> --threshold <threshold> --comparison-operator <operator> --evaluation-periods <evaluation-periods> --alarm-actions <action-arn>
  ```

- **List CloudWatch alarms**:
  ```bash
  aws cloudwatch describe-alarms
  ```

- **Get CloudWatch metrics**:
  ```bash
  aws cloudwatch get-metric-statistics --namespace <namespace> --metric-name <metric-name> --dimensions Name=InstanceId,Value=<instance-id> --start-time <start-time> --end-time <end-time> --period <period> --statistics <statistics>
  ```

- **List CloudWatch logs**:
  ```bash
  aws logs describe-log-groups
  ```

### **7. RDS (Relational Database Service)**

- **Create an RDS instance**:
  ```bash
  aws rds create-db-instance --db-instance-identifier <instance-name> --db-instance-class db.t2.micro --engine mysql --allocated-storage 20 --master-username <username> --master-user-password <password> --vpc-security-group-ids <sg-id>
  ```

- **Describe RDS instances**:
  ```bash
  aws rds describe-db-instances
  ```

- **Delete an RDS instance**:
  ```bash
  aws rds delete-db-instance --db-instance-identifier <instance-name> --skip-final-snapshot
  ```

### **8. VPC (Virtual Private Cloud)**

- **Create a VPC**:
  ```bash
  aws ec2 create-vpc --cidr-block <cidr-block>
  ```

- **Describe VPCs**:
  ```bash
  aws ec2 describe-vpcs
  ```

- **Create a subnet**:
  ```bash
  aws ec2 create-subnet --vpc-id <vpc-id> --cidr-block <cidr-block>
  ```

- **Create a security group**:
  ```bash
  aws ec2 create-security-group --group-name <sg-name> --description "<description>" --vpc-id <vpc-id>
  ```

- **Create a route table**:
  ```bash
  aws ec2 create-route-table --vpc-id <vpc-id>
  ```

### **9. EBS (Elastic Block Store)**

- **Create an EBS volume**:
  ```bash
  aws ec2 create-volume --availability-zone <zone> --size <size> --volume-type gp2
  ```

- **Attach an EBS volume to an instance**:
  ```bash
  aws ec2 attach-volume --volume-id <volume-id> --instance-id <instance-id> --device /dev/sdh
  ```

- **Describe EBS volumes**:
  ```bash
  aws ec2 describe-volumes
  ```

- **Delete an EBS volume**:
  ```bash
  aws ec2 delete-volume --volume-id <volume-id>
  ```

### **10. CloudFormation**

- **Create a CloudFormation stack**:
  ```bash
  aws cloudformation create-stack --stack-name <stack-name> --template-body file://<template-file>.json
  ```

- **Describe CloudFormation stacks**:
  ```bash
  aws cloudformation describe-stacks
  ```

- **Delete a CloudFormation stack**:
  ```bash
  aws cloudformation delete-stack --stack-name <stack-name>
  ```

### **11. SNS (Simple Notification Service)**

- **Create an SNS topic**:
  ```bash
  aws sns create-topic --name <topic-name>
  ```

- **List SNS topics**:
  ```bash
  aws sns list-topics
  ```

- **Publish a message to an SNS topic**:
  ```bash
  aws sns publish --topic-arn <topic-arn> --message "Your message"
  ```

### **12. SQS (Simple Queue Service)**

- **Create an SQS queue**:
  ```bash
  aws sqs create-queue --queue-name <queue-name>
  ```

- **Send a message to an SQS queue**:
  ```bash
  aws sqs send-message --queue-url <queue-url> --message-body "Your message"
  ```

- **Receive messages from an SQS queue**:
  ```bash
  aws sqs receive-message --queue-url <queue-url>
  ```

### **13. ECS (Elastic Container Service)**

- **Create an ECS cluster**:
  ```bash
  aws ecs create-cluster --cluster-name <cluster-name>
  ```

- **List ECS clusters**:
  ```bash
  aws ecs list-clusters
  ```

- **Register an ECS task definition**:
  ```bash
  aws ecs register-task-definition --family <task-family> --container-definitions file://<container-definition>.json
  ```

- **Run a task on ECS**:
  ```bash
  aws ecs run-task --cluster <cluster-name> --task-definition <task-definition> --count 1
  ```

---

These are just the basic commands to interact with AWS services via the AWS CLI. For more advanced commands and options, you can always refer to the official

 [AWS CLI documentation](https://docs.aws.amazon.com/cli/latest/reference/).