---
Title: Docker Inspect Output
date: 2024-12-29
tags:
  - reading_tasks
  - docker
---

Output of Mysql container from [[DevOps/Tasks Done/Task 3 Create Mysql Container]] 
### Inspecting a container
`docker inspect <container-id>`

```sql
[
  {
    "Id": "3ce6ffd3357d7d78a4fff68218ea477ef0bcc3a747153cb93143e128bb21e4a3",
    "Created": "2024-12-29T12:46:23.52003502Z",
    "Path": "docker-entrypoint.sh",
    "Args": [
      "mysqld"
    ],
    "State": {
      "Status": "running",
      "Running": true,
      "Paused": false,
      "Restarting": false,
      "OOMKilled": false,
      "Dead": false,
      "Pid": 13864,
      "ExitCode": 0,
      "Error": "",
      "StartedAt": "2024-12-29T12:46:23.928523535Z",
      "FinishedAt": "0001-01-01T00:00:00Z"
    },
    "Image": "sha256:56a8c14e14044b8ec7ffb4dd165c8dbe10d4c6ba3d9e754f0c906f52a0b5b4fb",
    "ResolvConfPath": "/var/lib/docker/containers/3ce6ffd3357d7d78a4fff68218ea477ef0bcc3a747153cb93143e128bb21e4a3/resolv.conf",
    "HostnamePath": "/var/lib/docker/containers/3ce6ffd3357d7d78a4fff68218ea477ef0bcc3a747153cb93143e128bb21e4a3/hostname",
    "HostsPath": "/var/lib/docker/containers/3ce6ffd3357d7d78a4fff68218ea477ef0bcc3a747153cb93143e128bb21e4a3/hosts",
    "LogPath": "/var/lib/docker/containers/3ce6ffd3357d7d78a4fff68218ea477ef0bcc3a747153cb93143e128bb21e4a3/3ce6ffd3357d7d78a4fff68218ea477ef0bcc3a747153cb93143e128bb21e4a3-json.log",
    "Name": "/mysql_container",
    "RestartCount": 0,
    "Driver": "overlay2",
    "Platform": "linux",
    "MountLabel": "",
    "ProcessLabel": "",
    "AppArmorProfile": "",
    "ExecIDs": null,
    "HostConfig": {
      "Binds": [
        "mysql_data:/var/lib/mysql"
      ],
      "ContainerIDFile": "",
      "LogConfig": {
        "Type": "json-file",
        "Config": {}
      },
      "NetworkMode": "default",
      "PortBindings": {
        "3306/tcp": [
          {
            "HostIp": "",
            "HostPort": "3306"
          }
        ]
      },
      "RestartPolicy": {
        "Name": "no",
        "MaximumRetryCount": 0
      },
      "AutoRemove": false,
      "VolumeDriver": "",
      "VolumesFrom": null,
      "ConsoleSize": [
        30,
        120
      ],
      "CapAdd": null,
      "CapDrop": null,
      "CgroupnsMode": "private",
      "Dns": [],
      "DnsOptions": [],
      "DnsSearch": [],
      "ExtraHosts": null,
      "GroupAdd": null,
      "IpcMode": "private",
      "Cgroup": "",
      "Links": null,
      "OomScoreAdj": 0,
      "PidMode": "",
      "Privileged": false,
      "PublishAllPorts": false,
      "ReadonlyRootfs": false,
      "SecurityOpt": null,
      "UTSMode": "",
      "UsernsMode": "",
      "ShmSize": 67108864,
      "Runtime": "runc",
      "Isolation": "",
      "CpuShares": 0,
      "Memory": 0,
      "NanoCpus": 0,
      "CgroupParent": "",
      "BlkioWeight": 0,
      "BlkioWeightDevice": [],
      "BlkioDeviceReadBps": [],
      "BlkioDeviceWriteBps": [],
      "BlkioDeviceReadIOps": [],
      "BlkioDeviceWriteIOps": [],
      "CpuPeriod": 0,
      "CpuQuota": 0,
      "CpuRealtimePeriod": 0,
      "CpuRealtimeRuntime": 0,
      "CpusetCpus": "",
      "CpusetMems": "",
      "Devices": [],
      "DeviceCgroupRules": null,
      "DeviceRequests": null,
      "MemoryReservation": 0,
      "MemorySwap": 0,
      "MemorySwappiness": null,
      "OomKillDisable": null,
      "PidsLimit": null,
      "Ulimits": [
        {
          "Name": "nofile",
          "Hard": 65536,
          "Soft": 32768
        }
      ],
      "CpuCount": 0,
      "CpuPercent": 0,
      "IOMaximumIOps": 0,
      "IOMaximumBandwidth": 0,
      "MaskedPaths": [
        "/proc/asound",
        "/proc/acpi",
        "/proc/kcore",
        "/proc/keys",
        "/proc/latency_stats",
        "/proc/timer_list",
        "/proc/timer_stats",
        "/proc/sched_debug",
        "/proc/scsi",
        "/sys/firmware",
        "/sys/devices/virtual/powercap"
      ],
      "ReadonlyPaths": [
        "/proc/bus",
        "/proc/fs",
        "/proc/irq",
        "/proc/sys",
        "/proc/sysrq-trigger"
      ]
    },
    "GraphDriver": {
      "Data": {
        "LowerDir": "/var/lib/docker/overlay2/12d00f10d37b859750c2db62bb19bd6f3cde4bdca742ecf8a77a7c00fe912f4f-init/diff:/var/lib/docker/overlay2/96c958faea5ea8ce734cd4db5008bb2188c285dce8190a8c7d35528a9e2ad055/diff:/var/lib/docker/overlay2/643ab6a924a7f65786e4033a2c82e8815cbca24318f429d9f62600d0e7e955a1/diff:/var/lib/docker/overlay2/a9e3b51cd314aa5cad0258b1330d9ca358ff9e4f063ed45f34948ff834b39c0a/diff:/var/lib/docker/overlay2/37efbaa9117f660d35ed59ca9683c1c22a545a8be5621032781bd59467451a29/diff:/var/lib/docker/overlay2/ea28ca7d3354a82731cf3e4947821e814414353c8b431189aec28a2e758946cd/diff:/var/lib/docker/overlay2/729ec68eb4d4f5273a13a068bb24d70d34dcb160fceb795f3058054552b28174/diff:/var/lib/docker/overlay2/6876ecc19a1ae8a61be41a8f298e9e0a012c0ab952944a4923ac46559c32ed3c/diff:/var/lib/docker/overlay2/8b4ab94e45bbe1ab2068b4488f60434de5788dcd4626f2eda8ccd367e2c513ac/diff:/var/lib/docker/overlay2/06533c7033b5c8d5069139b433e42842ebadf121567da334c956001cd942a139/diff:/var/lib/docker/overlay2/d01a0a333a0ac1376c37feec0c1cb771b28631b213fb399ed12ff685085c4b71/diff",
        "MergedDir": "/var/lib/docker/overlay2/12d00f10d37b859750c2db62bb19bd6f3cde4bdca742ecf8a77a7c00fe912f4f/merged",
        "UpperDir": "/var/lib/docker/overlay2/12d00f10d37b859750c2db62bb19bd6f3cde4bdca742ecf8a77a7c00fe912f4f/diff",
        "WorkDir": "/var/lib/docker/overlay2/12d00f10d37b859750c2db62bb19bd6f3cde4bdca742ecf8a77a7c00fe912f4f/work"
      },
      "Name": "overlay2"
    },
    "Mounts": [
      {
        "Type": "volume",
        "Name": "mysql_data",
        "Source": "/var/lib/docker/volumes/mysql_data/_data",
        "Destination": "/var/lib/mysql",
        "Driver": "local",
        "Mode": "z",
        "RW": true,
        "Propagation": ""
      }
    ],
    "Config": {
      "Hostname": "3ce6ffd3357d",
      "Domainname": "",
      "User": "",
      "AttachStdin": false,
      "AttachStdout": true,
      "AttachStderr": true,
      "ExposedPorts": {
        "3306/tcp": {},
        "33060/tcp": {}
      },
      "Tty": false,
      "OpenStdin": false,
      "StdinOnce": false,
      "Env": [
        "MYSQL_USER=name",
        "MYSQL_PASSWORD=passwd",
        "MYSQL_RANDOM_ROOT_PASSWORD=yes",
        "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
        "GOSU_VERSION=1.17",
        "MYSQL_MAJOR=innovation",
        "MYSQL_VERSION=9.1.0-1.el9",
        "MYSQL_SHELL_VERSION=9.1.0-1.el9"
      ],
      "Cmd": [
        "mysqld"
      ],
      "Image": "mysql:latest",
      "Volumes": {
        "/var/lib/mysql": {}
      },
      "WorkingDir": "/",
      "Entrypoint": [
        "docker-entrypoint.sh"
      ],
      "OnBuild": null,
      "Labels": {}
    },
    "NetworkSettings": {
      "Bridge": "",
      "SandboxID": "86cf8ccab46e8354b1949fbc9c3c96452864b775418ee65163a356bb7de1eaac",
      "SandboxKey": "/var/run/docker/netns/86cf8ccab46e",
      "Ports": {
        "3306/tcp": [
          {
            "HostIp": "0.0.0.0",
            "HostPort": "3306"
          },
          {
            "HostIp": "::",
            "HostPort": "3306"
          }
        ],
        "33060/tcp": null
      },
      "HairpinMode": false,
      "LinkLocalIPv6Address": "",
      "LinkLocalIPv6PrefixLen": 0,
      "SecondaryIPAddresses": null,
      "SecondaryIPv6Addresses": null,
      "EndpointID": "b28accc98581fb0504cd3e243023616b47126553a7b2c69ef1b443c351ad7fe2",
      "Gateway": "172.17.0.1",
      "GlobalIPv6Address": "",
      "GlobalIPv6PrefixLen": 0,
      "IPAddress": "172.17.0.2",
      "IPPrefixLen": 16,
      "IPv6Gateway": "",
      "MacAddress": "02:42:ac:11:00:02",
      "Networks": {
        "bridge": {
          "IPAMConfig": null,
          "Links": null,
          "Aliases": null,
          "MacAddress": "02:42:ac:11:00:02",
          "NetworkID": "1306a6d500d7b8f9a7da615852fab3d6ee12750f0d8550e6292d8ed5b5850930",
          "EndpointID": "b28accc98581fb0504cd3e243023616b47126553a7b2c69ef1b443c351ad7fe2",
          "Gateway": "172.17.0.1",
          "IPAddress": "172.17.0.2",
          "IPPrefixLen": 16,
          "IPv6Gateway": "",
          "GlobalIPv6Address": "",
          "GlobalIPv6PrefixLen": 0,
          "DriverOpts": null,
          "DNSNames": null
        }
      }
    }
  }
]
```

### Explanation
The `docker inspect` command provides a detailed view of a Docker object's configuration. This could be a container, image, network, volume, etc. You've provided the output for a container. Let's break down the key components:

**1. Id:** `3ce6ffd3357d7d78a4fff68218ea477ef0bcc3a747153cb93143e128bb21e4a3`

- This is the unique identifier for your container.

**2. Created:** `2024-12-29T12:46:23.52003502Z`

- Timestamp indicating when the container was created (in UTC).

**3. Path:** `docker-entrypoint.sh`

- This is the default command that will be executed within the container when it starts. Entrypoint scripts are useful for setting up the container environment, running services, or executing other tasks.

**4. Args:** `["mysqld"]`

- These are the arguments passed to the `Path` (entrypoint). In this case, "mysqld" is likely the command to start the MySQL server.

**5. State:**

- **Status:** `running` - Current state of the container.
- **Running:** `true` - Indicates if the container is currently running.
- **Paused:** `false` - Indicates if the container is paused.
- **Restarting:** `false` - Indicates if the container is in the process of restarting.
- **OOMKilled:** `false` - Indicates if the container was killed due to running out of memory (Out Of Memory).
- **Dead:** `false` - Indicates if the container has exited.
- **Pid:** `13864` - Process ID of the main process running inside the container.
- **ExitCode:** `0` - Exit code of the container (0 usually means success).
- **Error:** `""` - Any error message associated with the container's state.
- **StartedAt:** `2024-12-29T12:46:23.928523535Z` - Timestamp when the container was started.
- **FinishedAt:** `0001-01-01T00:00:00Z` - Timestamp when the container finished (if applicable).

**6. Image:** `sha256:56a8c14e14044b8ec7ffb4dd165c8dbe10d4c6ba3d9e754f0c906f52a0b5b4fb`

- The ID (SHA256 hash) of the image that was used to create this container.

**7. ResolvConfPath, HostnamePath, HostsPath, LogPath:**

- Paths to files within the container's filesystem that handle DNS resolution, hostname, host mappings, and container logs.

**8. Name:** `/mysql_container`

- The name you assigned to the container when you created it.

**9. RestartCount:** `0`

- Number of times the container has been restarted.

**10. Driver:** `overlay2`

- The storage driver used for the container's filesystem layers.

**11. Platform:** `linux`

- The platform (OS) for which the container was built.

**12. MountLabel, ProcessLabel, AppArmorProfile:** - Security-related labels and profiles.

**13. ExecIDs:** `null` - List of IDs of exec instances that have been run in this container (if any).

**14. HostConfig:** This section contains container settings that are specific to the host machine where the container is running:

```
- **Binds:** `["mysql_data:/var/lib/mysql"]` -  Shows volumes mounted inside the container. Here, a volume named "mysql_data" is mounted to `/var/lib/mysql` inside the container. This is often used for persistent storage.
- **LogConfig:** Configuration for container logging.
- **NetworkMode:** `default` - Networking mode for the container.
- **PortBindings:** `{"3306/tcp": [{"HostIp": "", "HostPort": "3306"}]}` -  Port mappings between the host and the container. This exposes the container's port 3306 on the host's port 3306.
- **RestartPolicy:** `{"Name": "no", "MaximumRetryCount": 0}` - Container restart policy (in this case, it won't restart automatically).
- **AutoRemove:** `false` - Whether the container should be automatically removed when it exits.
- **[Many other settings]:**  Resource limits (memory, CPU), security options, and other low-level configurations.
```

**15. GraphDriver:** - **Data:** Information about the graph driver (storage driver) used by the container.

**16. Mounts:** - Detailed information about the mounts configured for the container, including the source, destination, and options.

**17. Config:** This section describes the container's configuration, which is defined by the image and any modifications you made:

```
- **Hostname:** `3ce6ffd3357d` - Hostname of the container.
- **Domainname:**  Domain name of the container.
- **User:** User that the container runs as.
- **AttachStdin, AttachStdout, AttachStderr:**  Whether to attach to standard input/output/error streams.
- **ExposedPorts:**  Ports that the container exposes (may or may not be published to the host).
- **Tty:**  Whether the container has a pseudo-TTY allocated.
- **OpenStdin:** Whether to keep STDIN open even if not attached.
- **Env:** `["MYSQL_USER=name", "MYSQL_PASSWORD=passwd", ...]` - Environment variables set within the container.
- **Cmd:** `["mysqld"]` -  The command to be executed when the container starts.
- **Image:** `mysql:latest` - The image the container was created from.
- **Volumes:** Volumes defined in the container configuration.
- **WorkingDir:** `/` - The working directory inside the container.
- **Entrypoint:** `["docker-entrypoint.sh"]` - The entrypoint script for the container.
- **OnBuild:**  Triggers that execute in the context of the image build.
- **Labels:**  Metadata labels associated with the container.
```

**18. NetworkSettings:** This section provides details about the container's network configuration:

```
- **Bridge:**  Name of the bridge network the container is attached to.
- **SandboxID, SandboxKey:** Information related to the container's network namespace.
- **Ports:**  Details about the ports that are published to the host.
- **[Other network settings]:** IP address, MAC address, gateway, and other network-related information.
```

If you have a specific question about any of these elements, feel free to ask! I'm here to help you understand your Docker container's configuration.