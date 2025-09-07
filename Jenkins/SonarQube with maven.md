---
Title: SonarQube with Maven
date: 2025-02-16
tags:
  - sonarqube
  - maven
---

![sonar](https://miro.medium.com/v2/resize:fit:720/format:webp/1*KOadiTidZoHtrfanE3Ck5A.png)


Sonar provides a comprehensive code quality and security analysis solution to scan your IaC files in your managed cloud environments to review a wide range of possible issues or security vulnerabilities.
# Introduction

SonarQube is an open-source platform developed by SonarSource for continuous inspection of code quality to perform automatic reviews with static analysis of code to detect [bugs](https://www.techopedia.com/definition/3758/bug), [code smells](https://en.wikipedia.org/wiki/Code_smell), and [security vulnerabilities](https://owasp.org/www-community/vulnerabilities/) on 20+ programming languages.

> It can report duplicated code, coding standards, unit tests, code coverage, code complexity and comments.

> The only prerequisite for running SonarQube is to have Java ([Oracle JRE 11](https://www.oracle.com/java/technologies/javase-jre8-downloads.html) or [OpenJDK 11](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)) installed on your machine.

# Installation

Using docker run sonarqube container
```
docker run -d --name sonarqube -p 9000:9000 sonarqube
```
In your web browser, connect to [http://localhost:9000](http://localhost:9000) to access the SonarQube web interface.

Use the following default credentials to log in:

```
Username: admin  
Password: admin
```

You'll probably prompted to change the default password

- To run sonar scan against our locally hosted code select `manually` option

- Enter the **token name** and click the **"Generate"** button. You will get the sonar token.

- Save that token and Click **"Continue"**.
- Select **Maven** and copy the code

and open terminal and navigate to your locally hosted code's directory
and run that command

```sh
mvn clean verify sonar:sonar \
  -Dsonar.projectKey=student \
  -Dsonar.projectName='student' \
  -Dsonar.host.url=http://3.137.177.165:32768 \
  -Dsonar.token=sqp_3584391716cf8fbc01eeea4e17d34b35b07d5a2f
```

and then check sonarqube dashboard for code analysis report.

