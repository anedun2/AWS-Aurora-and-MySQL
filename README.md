# AWS-Aurora-and-MySQL
We are going to connect to AWS Aurora database through Terminal Window or Command Line Interface(CLI) using MySQL

**As a prerequisite, we should have created a DB instance in AWS RDS** [Follow link for AWS docs](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.CreateInstance.html)  

## Steps 
1. Identify your data
2. Connect to Aurora DB using MySQL
3. Create a database
4. Create a table
5. Load the data

## 1. Identify your data
We are going to use Employee data "Employee.csv"

## 2. Connect to Aurora DB using MySQL

Example command to connect to the DB instance:
```bash
mysql -h database-1.cluster-cqpfqjdj8sso.us-east-1.rds.amazonaws.com -P 3306 -u admin -p --local-infile ProjectDB -A
```
where,
```-h``` is the host or Endpoint name(```database-1.cluster-cqpfqjdj8sso.us-east-1.rds.amazonaws.com```) from DB instance

```-u``` is the master username used while creating the cluster

```-p``` prompts for password

```--local-infile``` allows to load data from the computer to the cloud

```ProjectDB``` is the custom name of the database created while creating the DB cluster

## 3. Create a database

Create a Database using ```CREATE DATABASE database_name;``` if no database was created when creating a DB cluster. Or else move on to the next step.

## 4. Create a table

Run this in the CLI to create a Employee Table in the Database

```CREATE TABLE Employee (ID INT NOT NULL AUTO_INCREMENT, lastName VARCHAR(25) NOT NULL, firstName VARCHAR(25) NOT NULL, email VARCHAR(255) NOT NULL, phone VARCHAR(255) NOT NULL, department INT NOT NULL, position VARCHAR(255) NOT NULL, team VARCHAR(255) NOT NULL,  PRIMARY KEY (ID));```

## 5. Load the data

Run this in the CLI to load the data into Employee Table in the Database

```LOAD DATA LOCAL INFILE '/Users/arun/Desktop/Employee.csv' INTO TABLE Employee FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n' IGNORE 1 ROWS;```

