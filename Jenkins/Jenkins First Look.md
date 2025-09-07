---
Title: Jenkins First Look
date: 2025-02-25
tags:
  - jenkins
---

#### What is Jenkins?

Jenkins is a CI/CD Automation Tool that automates the Continuous Integration and Continuous development part of Software development process.
## Core Concepts

- **Automation Server**: Jenkins automates repetitive technical tasks involved in building, testing, and deploying software.
- **Continuous Integration**: Jenkins can automatically build and test code changes whenever developers push updates to a repository, helping catch issues early.
- **Continuous Delivery/Deployment**: Jenkins can automatically deploy applications to testing or production environments.

## Key Features

- **Pipeline Support**: Define your build/test/deploy pipelines as code using a Jenkinsfile.
- **Distributed Builds**: Jenkins can distribute work across multiple machines.
- **Extensibility**: Thousands of plugins available to integrate with various tools and platforms.
- **Web Interface**: Easy-to-use dashboard for monitoring jobs and builds.
- **Master-Agent Architecture**: A master server coordinates with agent nodes to execute jobs.

## Basic Components

- **Jobs/Projects**: Individual automated tasks configured in Jenkins.
- **Builds**: Results of a single run of a project.
- **Plugins**: Extensions that add functionality to Jenkins.
- **Nodes**: Machines where Jenkins executes jobs.
- **Workspace**: Directory where Jenkins places files for a build.

## 2. Creating and Configuring Jobs/Pipelines

**Freestyle Projects:**

- Navigate to Dashboard > New Item > Freestyle project
- Configure source code management, build triggers, build steps, and post-build actions
- Build steps can run shell commands, batch scripts, or other build tools

**Pipeline Projects:**

- Create with Dashboard > New Item > Pipeline
- Define pipeline either through Pipeline script in the UI or by referencing a Jenkinsfile in SCM
- Supports both Declarative and Scripted pipeline syntax

## 1. Jenkins Pipeline Syntax and Jenkinsfiles

**Declarative Pipeline:**

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'mvn deploy'
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed'
        }
        success {
            echo 'Successfully completed'
        }
        failure {
            echo 'Failed'
        }
    }
}
```

**Scripted Pipeline:**
```groovy
node {
    stage('Build') {
        echo 'Building....'
        sh 'mvn clean compile'
    }
    stage('Test') {
        echo 'Testing....'
        sh 'mvn test'
    }
}
```
## 2. Managing Plugins

- Access via Dashboard > Manage Jenkins > Plugins
- Available plugins tab shows installable plugins
- Installed tab shows current plugins and available updates
- Advanced tab allows manual plugin upload
- Jenkins must often be restarted after plugin installation
- Core plugins: Git, Pipeline, Blue Ocean, Docker, Credentials

## 3. Master-Agent Setup
### Jenkins Master-Agent Setup

Jenkins uses a master-agent architecture to distribute builds across multiple machines, improving performance and allowing specialized environments for different build types.
#### Core Concepts

##### Master Server
- Central controlling server that:
    - Hosts the web UI
    - Stores all configurations
    - Schedules builds
    - Dispatches builds to agents
    - Monitors agents and collects build results

##### Agent Nodes
- Separate machines that:
    - Execute the actual build jobs
    - Report results back to the master
    - Can be configured for specific environments (Windows, Linux, macOS)
    - Can have specialized hardware (high CPU, GPU, memory)

### Setting Up Agents

#### Method 1: SSH Connection

1. **On master**: Navigate to Dashboard > Manage Jenkins > Manage Nodes and Clouds > New Node
2. Configure node name, permanent agent, and description
3. Set number of executors (parallel jobs the agent can run)
4. Configure remote root directory for workspace
5. Set launch method to "Launch agents via SSH"
6. Provide host details and credentials
7. Configure host key verification strategy

#### Method 2: JNLP Connection

1. **On master**: Create a node as above, but select "Launch agent by connecting it to the master"
2. Configure agent as a service on the agent machine using the generated command

#### Method 3: Docker Agents

1. Install Docker plugin
2. Configure cloud provider in Jenkins (Dashboard > Manage Jenkins > Manage Nodes and Clouds > Configure Clouds)
3. Add Docker templates defining images to be used as agents
- **Master**: Coordinates jobs, serves UI, stores configurations
- **Agents**: Execute the actual builds
- Add agents via Dashboard > Manage Jenkins > Manage Nodes and Clouds
- Connection methods include SSH, JNLP, Docker
- Configure node labels to direct specific jobs to appropriate agents

## 4. SCM Integration

- **Git Integration**: Use the Git plugin to connect to repositories
- Enable branch discovery for multibranch pipelines
- Configure webhook triggers from GitHub/GitLab/Bitbucket
- Integrate with pull request builders to test PRs automatically
- Access credentials via Jenkins Credentials store

## 5. CI/CD Best Practices

- Keep pipelines in version control (Pipeline as Code)
- Make builds reproducible and self-contained
- Fail fast - test critical components early
- Keep the pipeline fast (< 10 minutes ideally)
- Use parallel stages for independent tasks
- Implement proper test coverage
- Use artifacts and fingerprinting for traceability
- Implement proper security scanning

## 6. Monitoring

- Jenkins built-in monitoring via Dashboard > Manage Jenkins > System Information
- Prometheus plugin for metrics collection
- Monitor file system space for artifacts
- Set up email/Slack notifications for build failures
- Monitor agent connectivity and performance
- Regular backup of JENKINS_HOME directory

## 7. Troubleshooting

- Check Console Output for failing jobs
- Review Jenkins system logs (Dashboard > Manage Jenkins > System Log)
- Verify agent connectivity issues with agent logs
- Clean workspaces when experiencing strange build failures
- Check for plugin compatibility issues
- Isolate pipeline stages to identify problem areas
- Use Pipeline Syntax Generator for complex pipeline steps
