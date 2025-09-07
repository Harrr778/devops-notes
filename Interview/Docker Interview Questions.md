---
Title: Docker Interview Questions
date: 2025-02-28
tags:
  - docker
  - interview_questions
---
**Fundamentals**

<details>
<summary>1. What is docker and why is it used?</summary><br>
Docker is a containerization platform that allows developers to package, ship and run application in container format.
Containers are lightweight and portable making it easier to develop, test and deploy application.
</details>

<details><summary>2. Explain the difference between docker, images and containers.</summary>

A Docker image is a read-only template with instructions for creating a Docker container. A container is a runnable instance of an image, providing an isolated environment for the application.
</details>
<details><summary>3. what is dockerfile and what are its essential components?</summary>
A Dockerfile is a text file that contains instruction to build an image that containers can use.
</details>
<details><summary>4. what is docker hub, and how is it used?</summary>
Docker Hub is a cloud-based registry service provided by Docker for finding and sharing container images. It acts as a central repository for both public and private Docker images.
</details>
<details><summary>5. what are docker volumes, and how do they differ from bind mounts?</summary>

</details>
1. Explain the concept of docker networking.
2. What are docker layers, and how do they contribute to image efficiency?
3. what is the purpose of docker-compose.yml file?
4. explain the difference between docker and virtual machines.
5. what are docker registries?
6. what is the difference between the COPY and ADD instruction in a dockerfile?
7. what are the benefits of using multi-stage builds in docker?

**Docker Commands & Operations:**

- How do you build a Docker image?
- How do you run a Docker container?
- How do you list running and stopped containers?
- How do you remove Docker images and containers?
- How do you inspect a Docker container?
- How do you view Docker container logs?
- How do you expose ports from a Docker container?
- How do you create a custom Docker network?
- How do you use Docker volumes to persist data?
- How do you troubleshoot a failing Docker container?
- How do you tag a Docker image?
- How do you push a Docker image to Docker Hub?
- How do you pull a docker image from a registry?
- How do you use the docker exec command?

**Docker Compose & Orchestration:**

- What is Docker Compose, and how does it simplify multi-container deployments?
- How do you define services, networks, and volumes in a `docker-compose.yml` file?
- How do you scale Docker Compose services?
- How do you manage environment variables in Docker Compose?
- How does Docker Compose interact with Docker networks?
- What is the difference between docker compose up, and docker compose up -d?
- How does docker compose override files work?
- How does docker work with orchestration tools like Kubernetes or Docker Swarm?

**Security & Best Practices:**

- What are some Docker security best practices?
- How do you secure Docker containers?
- How do you minimize the size of Docker images?
- How do you manage Docker secrets?
- How do you implement resource limits for Docker containers?
- What are the security implications of running Docker containers as root?
- How would you scan a docker image for vulnerabilities?

**Troubleshooting & Advanced Topics:**

- How do you troubleshoot Docker networking issues?
- How do you debug a Dockerfile build process?
- How do you monitor Docker container performance?
- What are Docker system prune commands?
- How would you implement a CI/CD pipeline with Docker?
- How does Docker relate to container runtimes?
- What are some of the common errors encountered when using docker and how would you resolve them?
