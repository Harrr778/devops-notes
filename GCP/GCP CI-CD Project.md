---
Title: CI-CD GCP Project
date: 2025-03-27
tags:
  - GCP
  - CI/CD
---
This is raw notes from GCP CI/CD Handson from Intel Learning Platform [^1]
## Push our code to github repository

Dockerfile
```Dockerfile
FROM python:3.11-slim-bullseye
WORKDIR /app
COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt
COPY . .
EXPOSE 8080
CMD [ "python3", "-m", "helloworld", "run", "--host=0.0.0.0" ]
```

Our source code
helloworld.py
```python
from flask import Flask

import random

app = Flask(__name__)

def calculate_lucky_numbers():

    numbers = random.sample(range(1,53),5)
    return str(numbers)[1:-1]

@app.route("/")
def hello():

    message = "<h1 style=\"color: #001cff;\">Hello world from intel cloud.U</h1>"
    message += "<h2>Version 2.0</h2>"
    message += "<p> Your lucky numbers are <b>"
    message += calculate_lucky_numbers() + "</b></p>"
    return (message)

app.run(host='0.0.0.0', port=8080, debug=True)
```

requirements.txt
```txt
flask
```


## connect the github repo to GCP Cloud Source Repository

## goto cloud build to configure a trigger
![[{14D6A024-F203-4EA8-A7FD-5DC718C88048} 1.png]]
- setup build trigger button
create trigger 
- name
- Event: Push to a branch
- source: github
- branch main
- configuration: cloud build
- location: repository
- cloud build configuration file location:
   /cloudbuild.yaml 

## Create cloudbuild configuration file in git repo
cloudbuild.yaml
```
steps:
 # build the container image
 - name: 'gcr.io/cloud-builders/docker'
   args: ['build', '-t', 'gcr.io/$PROJECT_ID/helloworld:$COMMIT_SHA', '.']
 # push the container image to container registry
 - name: 'gcr.io/cloud-builders/docker'
   args: ['push', 'gcr.io/$PROJECT_ID/helloworld:$COMMIT_SHA']
 # Deploy container image to cloud Run
 - name: 'gcr.io/google.com/cloudsdktool/cloud-sdk'
   entrypoint: gcloud
   args:
   - 'run'
   - 'deploy'
   - 'hello-world-service'
   - '--image'
   - 'gcr.io/$PROJECT_ID/helloworld:$COMMIT_SHA'
   - '--region'
   - 'us-east1'
   - '--allow-unauthenticated'

images:
  - 'gcr.io/$PROJECT_ID/helloworld:$COMMIT_SHA'
```

## push to repo
## check for trigger

## check the build is running
![[{D887FA6C-FDC1-4335-8695-6348455C2344}.png]]
## look for container is stored in google container registry
![[{1F025C4B-9AAA-4AB4-9BFE-C01D52D0DACC}.png]]
# **Addressing Errors in Code**

In case some bugs has found in production release we can redirect the traffic to old revisions with cloud run by switching the 100% traffic flow to older revisions
![[{5CA67175-06A7-44F8-8719-3018C757F810}.png]]
![[{AB7100C3-BCE9-4388-9D39-10AF959ABF5F}.png]]

---
# References:
[^1]: Intel Cloud Learning Devops Training Course - [Link](https://partneruniversity.intel.com/learn/learning_plan/view/340/url)

Credly badge for the above course can be found here https://www.credly.com/org/intel/badge/cloud-devops

This Hands on is based on A book _Continuous Delivery with Docker and Jenkins: Create secure applications by building complete CI/CD pipelines”, which was written by Rafal Leszko._
