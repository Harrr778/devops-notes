---
Title: Read about docker.sock file
date: 2024-12-30
tags:
  - reading_tasks
  - docker
  - socket
---
## What is docker.sock file

Basically this file act as a bridge between docker daemon and docker client.
Its responsible for api communications between docker client and dockerd service that runs in the background.

So when you run `docker run nginx`
docker client send request to this file over at `/var/run/docker.sock` and then docker daemon which is constantly listening for this socket it receives the request and create container.

![[docker-sock-file.svg]]
### From Gemini Ai
The `docker.sock` file is a Unix socket that allows communication between the Docker client and the Docker daemon (the background process that manages containers). It acts like a bridge, enabling you to manage containers, images, networks, and more.

Here's a breakdown:

- **What is a socket?** A socket is a way for programs to communicate with each other, either on the same machine or over a network. Think of it like a phone line specifically for applications.
- **Why a socket instead of a network connection?** Using a Unix socket for communication between the client and daemon on the same host is more efficient and secure than using network-based protocols like HTTP or TCP.
- **How it works:** When you run a Docker command (e.g., `docker run`), the client sends the command to the `docker.sock` file. The Docker daemon, listening on the other end of the socket, receives the command and executes it.
- **Location:** The `docker.sock` file is typically located at `/var/run/docker.sock` on Linux systems.
- **Security:** The `docker.sock` file is usually owned by the root user and the docker group, which restricts access and enhances security.

**Key points to remember:**

- It's the primary way to interact with the Docker daemon.
- It enables efficient and secure communication.
- It's a critical component for managing Docker containers and images.
- Misusing or exposing the `docker.sock` file can lead to security risks.

If you're interested in diving deeper, I recommend checking out these resources:

- **Understanding /var/run/docker.sock:** [https://dev.to/piyushbagani15/understanding-varrundockersock-the-key-to-dockers-inner-workings-nm7](https://dev.to/piyushbagani15/understanding-varrundockersock-the-key-to-dockers-inner-workings-nm7)
- **What is Docker socket binding?** [https://www.geeksforgeeks.org/what-is-docker-socket-binding/](https://www.geeksforgeeks.org/what-is-docker-socket-binding/)
- **Docker Tips: about /var/run/docker.sock:** [https://www.geeksforgeeks.org/docker-tips-about-varrundockersock/](https://www.geeksforgeeks.org/docker-tips-about-varrundockersock/)

### Interesting Read From a Reddit user"

When you install docker in a machine. Two diffrent programs come in:

- Docker Client
- Docker Server

Docker Server receives commands over a socket (either over a network or through a "file")

Docker Client communicates over a network and sends message to the Docker server to say make a container, start a container, stop a container etc.

When the client and server are running on the same computer, they can connect through a special file called a socket. And since they can communicate through a file and Docker can efficiently share files between hosts and containers, it means you can run the client inside Docker itself.

Here is a sample:

```sh
docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock docker sh
```

This command creates a container that docker client installed within. And check the volume part: `-v /var/run/docker.sock:/var/run/docker.sock`

With `-v` flag it shares host `docker.sock` file so you can manipulate the containers within the host via a container.

```bash
docker run --rm -it ubuntu bash # Creates a new container via container 
```

Run `docker ps` on host terminal.

```bash
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS     NAMES
0f9e333b59fe   ubuntu    "bash"                   5 seconds ago    Up 4 seconds              zealous_wilson
b4a8af31416b   docker    "docker-entrypoint.s…"   16 minutes ago   Up 16 minutes             epic_elion
```

### From Brave Ai

Docker.sock file

The Docker.sock file, also known as the Docker socket, is a Unix domain socket (UDS) file used by Docker to communicate between the Docker daemon (dockerd) and the Docker client. It allows the client to send commands to the daemon and receive responses.

## Location

By default, the Docker.sock file is located at `/var/run/docker.sock` on Linux systems and `C:\ProgramData\docker\socket` on Windows systems.

## Functionality

The Docker.sock file enables the following:

1. **Command execution**: The Docker client sends commands (e.g., `docker run`, `docker ps`) to the daemon through the socket, which executes the requested action.
2. **Response retrieval**: The daemon sends responses (e.g., container output, error messages) back to the client through the socket.

## Security considerations

1. **Access control**: The Docker.sock file is owned by the `docker` group and has restrictive permissions by default, ensuring that only authorized users can access it.
2. **Encryption**: The communication between the client and daemon is not encrypted by default. To secure the socket, you can enable TLS encryption using the `--tls` and `--tlscert` flags when starting the daemon.

## Mounting the socket

You can mount the Docker.sock file inside a container using the `-v` flag when running the container. For example:

```bash
docker run -v /var/run/docker.sock:/var/run/docker.sock my-image
```

This allows the container to access the Docker socket and interact with the Docker daemon on the host system.

## Alternatives

If you need to access the Docker daemon remotely or securely, consider using a TCP socket (e.g., `dockerd -H tcp://0.0.0.0:2375`) or a proxy like Docker Compose or Kubernetes.

---
### Some External Links for good reads on this subject
1. https://lobster1234.github.io/2019/04/05/docker-socket-file-for-ipc/
2. https://stackoverflow.com/questions/35110146/what-is-the-purpose-of-the-file-docker-sock
3. https://www.educative.io/answers/var-run-dockersock