# How to build a simple todo-list application

This repo contains the sample application for building and testing a simple todo-list application.


## Tech Stack


- Frontend: React, Material UI.
- Backend: Node.js, Express
- Database: Mongo(running locally for storing tasks) running in a Docker container

## Project Structure

This project contains the following components:
- **/backend** - This directory contains the Node.js application that handles the server-side logic and interacts with the database. i
- **/frontend** - The frontend directory contains the React application that handles the user interface and interacts with the backend. 
- compose-native.yml - This compose file starts MongoDB.
  
## Development

1. Clone the repository

```
git clone https://github.com/dockersamples/todo-list-localstack-docker
```

2. Switch to todo-list-simple branch

```
git checkout todo-list-simple
```
```

3.  Run the Mongo container

```
docker compose -f compose-native.yml up -d --build
```

Open Docker Dashboard and check if Mongo is up and running


## Bring up Backend

```
cd backend/
npm install

```

Start the backend server:


```
node index.js
```

You will see the message that the backend service has successfully started at port 5000.



## Start the frontend

Open a new terminal and run the following command:

```
cd frontend/
npm run dev
```

By now, you should see the following message

```
VITE v5.4.2  ready in 110 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h + enter to show help

```

## Try adding a task and uploading the image


## Check the Mongo container logs

```
# mongosh
Current Mongosh Log ID: 66cb1093118d7d4cc1c76a8a
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.3.0
Using MongoDB:          7.0.12
Using Mongosh:          2.3.0

For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/


To help improve our products, anonymous usage data is collected and sent to MongoDB periodically (https://www.mongodb.com/legal/privacy-policy).
You can opt-out by running the disableTelemetry() command.

------
   The server generated these startup warnings when booting
   2024-08-25T10:58:46.918+00:00: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
   2024-08-25T10:58:47.668+00:00: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
   2024-08-25T10:58:47.668+00:00: /sys/kernel/mm/transparent_hugepage/enabled is 'always'. We suggest setting it to 'never' in this binary version
   2024-08-25T10:58:47.668+00:00: vm.max_map_count is too low
------

test> show dbs
admin   40.00 KiB
config  60.00 KiB
local   40.00 KiB
todos    8.00 KiB
test> use todos
switched to db todos
todos> db.todos.countDocuments()
2
todos> db.todos.countDocuments()
3
todos> 
```

## Stop the container services

```
docker compose -f compose-native.yml down
```

## Connecting to containerised LocalStack from a containerised Node app

```
docker compose -f compose.yml up -d --build
```

## Add a Sample S3 Bucket

Using the AWS CLI with LocalStack lets you interact with the emulated services exactly as you would with real AWS services. This helps ensure that your application behaves the same way in a local environment as it would in a production environment on AWS.


Let’s create a new S3 bucket within the LocalStack environment:


```
awslocal s3 mb s3://mysamplebucket
```

The command `s3 mb s3://mysamplebucket` tells the AWS CLI to create a new S3 bucket (mb stands for "make bucket"). The bucket is named `mysamplebucket`
It should show the following result:

```
make_bucket: mysamplebucket
```


## Try adding a task and uploading the image


![image](https://github.com/user-attachments/assets/55ca86c0-c83b-4f5e-83d2-0e87c97ba48a)

It shows the image is successfully uploaded.

## Check the LocalStack container logs

<img width="1337" alt="image" src="https://github.com/user-attachments/assets/e29f1a72-13a7-45d0-b55b-23a396916bfa">

## Check the Mongo container logs

```
# mongosh
Current Mongosh Log ID: 66cb1093118d7d4cc1c76a8a
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.3.0
Using MongoDB:          7.0.12
Using Mongosh:          2.3.0

For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/


To help improve our products, anonymous usage data is collected and sent to MongoDB periodically (https://www.mongodb.com/legal/privacy-policy).
You can opt-out by running the disableTelemetry() command.

------
   The server generated these startup warnings when booting
   2024-08-25T10:58:46.918+00:00: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
   2024-08-25T10:58:47.668+00:00: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
   2024-08-25T10:58:47.668+00:00: /sys/kernel/mm/transparent_hugepage/enabled is 'always'. We suggest setting it to 'never' in this binary version
   2024-08-25T10:58:47.668+00:00: vm.max_map_count is too low
------

test> show dbs
admin   40.00 KiB
config  60.00 KiB
local   40.00 KiB
todos    8.00 KiB
test> use todos
switched to db todos
todos> db.todos.countDocuments()
2
todos> db.todos.countDocuments()
3
todos> 
```
