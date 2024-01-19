# Dice-Assignment1-Part2
This Assignment based on Docker. In this part We will do Docker Containers with Commands

**Step 1: Using the docker image from Part 1**

```bash
docker images
```

REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
- random_fact   latest    84ba4bd82b9e   23 hours ago   1.07GB
<none>        <none>    5175a4fa914e   23 hours ago   1.07GB

we will use random_fact docker image for this assignment.


**Step 2: Run the Docker Container**

```bash
docker run -p 5000:89 random_fact
```

 * Serving Flask app 'random_fact'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:89
 * Running on http://172.17.0.2:89
Press CTRL+C to quit
172.17.0.1 - - [16/Jan/2024 09:42:07] "GET / HTTP/1.1" 200 -
172.17.0.1 - - [16/Jan/2024 09:42:07] "GET /favicon.ico HTTP/1.1" 404 -
172.17.0.1 - - [16/Jan/2024 09:42:19] "GET / HTTP/1.1" 200 -
172.17.0.1 - - [16/Jan/2024 09:42:22] "GET / HTTP/1.1" 200 -

**Step 3: Use Different Docker Container Commands**

```bash
docker ps
```

This command is used for list the running containers

CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS         PORTS                  NAMES
fd29ad768e21   random_fact   "python ./random_fac…"   3 seconds ago   Up 2 seconds   0.0.0.0:5000->89/tcp   mystifying_roentgen

```bash
docker stop
```

This command is used to stop the coontainer. we need to enter command with container name.

docker stop mystifying_roentgen 
mystifying_roentgen

```bash
docker exec
```

This command is used to run terminal insde the container.
docker exec -it elated_snyder sh

```bash
ls
```

* Dockerfile  README.md  myenv  random_fact.py  requirements.txt

```bash
docker logs
```

This command is used to see the container logs.

docker logs elated_snyder 
 * Serving Flask app 'random_fact'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:89
 * Running on http://172.17.0.2:89

Press CTRL+C to quit

```bash
docker restart
```

This command is used to restart the container.
we need to enter container name with restart.

* docker restart elated_snyder 
elated_snyder

* naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$

```bash
  docker ps
```

CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS          PORTS                  NAMES
117d420f36dc   random_fact   "python ./random_fac…"   6 minutes ago   Up 17 seconds   0.0.0.0:5000->89/tcp   elated_snyder

```bash
docker update
```

This command is used to update the resources of container Like RAM, CPU.

docker inspect --format '{{.HostConfig.Memory}} {{.HostConfig.MemorySwap}}' elated_snyder
0 0

```bash
docker update --cpu-shares 512 -m 1GB --memory-swap 1GB elated_snyder
elated_snyder
```

```bash
docker inspect --format '{{.HostConfig.Memory}} {{.HostConfig.MemorySwap}}
```
elated_snyder
1073741824 1073741824

```bash
docker update --cpu-shares 512 -m 500M --memory-swap 500M elated_snyder
```

elated_snyder

```bash
docker inspect --format '{{.HostConfig.Memory}} {{.HostConfig.MemorySwap}}' elated_snyder
524288000 524288000
```

```bash
docker top
```

docker top elated_snyder 
UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
root                2017                1990                0                   09:53               ?                   00:00:00            python ./random_fact.py

```bash
docker start
```

```bash
docker stop elated_snyder
```

elated_snyder

naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ docker start elated_snyder
elated_snyder

```bash
docker stats
```

CONTAINER ID   NAME            CPU %     MEM USAGE / LIMIT   MEM %     NET I/O       BLOCK I/O   PIDS
117d420f36dc   elated_snyder   0.01%     22.68MiB / 500MiB   4.54%     1.02kB / 0B   0B / 0B     1

```bash
docker pause
```

 docker pause elated_snyder 

elated_snyder

naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ docker ps
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS                       PORTS                  NAMES
117d420f36dc   random_fact   "python ./random_fac…"   56 minutes ago   Up About a minute (Paused)   0.0.0.0:5000->89/tcp   elated_snyder

```bash
docker unpause
```

docker unpause elated_snyder 

elated_snyder

naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ docker ps
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS         PORTS                  NAMES
117d420f36dc   random_fact   "python ./random_fac…"   57 minutes ago   Up 2 minutes   0.0.0.0:5000->89/tcp   elated_snyder

```bash
docker rename
```

```bash
docker rename elated_snyder random_python_app
```
naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ docker ps
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS         PORTS                  NAMES
117d420f36dc   random_fact   "python ./random_fac…"   58 minutes ago   Up 4 minutes   0.0.0.0:5000->89/tcp   random_python_app

```bash
docker inspect
```

```bash
docker inspect random_python_app 
```
[
    {
        "Id": "117d420f36dcfd6f08454fd06a783ddf0e67b71fe2fbf45a2e1d2e6eaa417692",
        "Created": "2024-01-16T09:47:32.990242846Z",
        "Path": "python",
        "Args": [
            "./random_fact.py"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 2441,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-01-16T10:41:46.667499672Z",
            "FinishedAt": "2024-01-16T10:41:37.59794512Z"
        },
        "Image": "sha256:84ba4bd82b9e554bbaf9168ccd461c6654ec2ce6147946ee33e576ce93326853",
        "ResolvConfPath": "/var/lib/docker/containers/117d420f36dcfd6f08454fd06a783ddf0e67b71fe2fbf45a2e1d2e6eaa417692/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/117d420f36dcfd6f08454fd06a783ddf0e67b71fe2fbf45a2e1d2e6eaa417692/hostname",
        "HostsPath": "/var/lib/docker/containers/117d420f36dcfd6f08454fd06a783ddf0e67b71fe2fbf45a2e1d2e6eaa417692/hosts",
        "LogPath": "/var/lib/docker/containers/117d420f36dcfd6f08454fd06a783ddf0e67b71fe2fbf45a2e1d2e6eaa417692/117d420f36dcfd6f08454fd06a783ddf0e67b71fe2fbf45a2e1d2e6eaa417692-json.log",
        "Name": "/random_python_app",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {
                "89/tcp": [
                    {
                        "HostIp": "",
                        "HostPort": "5000"
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
                63,
                102
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
            "CpuShares": 512,
            "Memory": 524288000,
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
            "MemorySwap": 524288000,
            "MemorySwappiness": null,
            "OomKillDisable": null,
            "PidsLimit": null,
            "Ulimits": null,
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
                "LowerDir": "/var/lib/docker/overlay2/24acb1c058c419050d4c58b7b4ab19312c96c7e124774159d91c2edbe2f57e15-init/diff:/var/lib/docker/overlay2/p834n87zrdvnjopxft0sucoiw/diff:/var/lib/docker/overlay2/rfchyu30x09mwe4phjc8jt4nj/diff:/var/lib/docker/overlay2/y6if7upc8nk915cv86737jj0d/diff:/var/lib/docker/overlay2/1749ea103af8c337dd0f797ea89bc2f3bd109a6b5d7ce648541f08344c15cffc/diff:/var/lib/docker/overlay2/a841c8504ecdb92dedc7b42d1364b38436c1dbcc8ba4c9f4b906457055f65a13/diff:/var/lib/docker/overlay2/a4afcbb299f1f62cfa627ca472c2796090d7844b69910c70dae6c2a958d75ae2/diff:/var/lib/docker/overlay2/157b778605435722afba45f39d70f571feb6dffeb24b9f4d569cac24eab0a74d/diff:/var/lib/docker/overlay2/5bcd7bd5811161eeb6180b2a9b5dc77eeabb6a1a75c7bcecb373c715b162a2cb/diff:/var/lib/docker/overlay2/810a1fad963c88da55873316e7a1d7dfce88946b7f5f40968b8cc29dda7884c6/diff:/var/lib/docker/overlay2/3bef767bb8c3cf17e1fe5ac496762a1c97bef16bf5fab7d0086b97400eef9c14/diff:/var/lib/docker/overlay2/32cd57d2d7b1f69c333b4196a65f279bb2c4c497632625f46884cb721558f16b/diff",
                "MergedDir": "/var/lib/docker/overlay2/24acb1c058c419050d4c58b7b4ab19312c96c7e124774159d91c2edbe2f57e15/merged",
                "UpperDir": "/var/lib/docker/overlay2/24acb1c058c419050d4c58b7b4ab19312c96c7e124774159d91c2edbe2f57e15/diff",
                "WorkDir": "/var/lib/docker/overlay2/24acb1c058c419050d4c58b7b4ab19312c96c7e124774159d91c2edbe2f57e15/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "117d420f36dc",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "89/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "LANG=C.UTF-8",
                "GPG_KEY=7169605F62C751356D054A26A821E680E5FA6305",
                "PYTHON_VERSION=3.12.1",
                "PYTHON_PIP_VERSION=23.2.1",
                "PYTHON_GET_PIP_URL=https://github.com/pypa/get-pip/raw/4cfa4081d27285bda1220a62a5ebf5b4bd749cdb/public/get-pip.py",
                "PYTHON_GET_PIP_SHA256=9cc01665956d22b3bf057ae8287b035827bfd895da235bcea200ab3b811790b6"
            ],
            "Cmd": [
                "python",
                "./random_fact.py"
            ],
            "Image": "random_fact",
            "Volumes": null,
            "WorkingDir": "/usr/scr/app",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {}
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "12c346ec0eea1952761732d23759bf043ef04dbaf477e8a1c591c09d1c40856e",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "89/tcp": [
                    {
                        "HostIp": "0.0.0.0",
                        "HostPort": "5000"
                    }
                ]
            },
            "SandboxKey": "/var/run/docker/netns/12c346ec0eea",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "d61580ed2c18f4c3f6d2cff4aa4885a4a45068b72d02499e795d561839591d80",
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
                    "NetworkID": "c105b0eb3d6db370a7774c0653a82d2283be25daf49044352006eaf9ed2d1ff5",
                    "EndpointID": "d61580ed2c18f4c3f6d2cff4aa4885a4a45068b72d02499e795d561839591d80",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DriverOpts": null
                }
            }
        }
    }
]
naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ 


```bash
docker port
```
docker ps 

CONTAINER ID   IMAGE         COMMAND                  CREATED              STATUS              PORTS                  NAMES
8727f3a40b1d   random_fact   "python ./random_fac…"   About a minute ago   Up About a minute   0.0.0.0:5000->89/tcp   confident_zhukovsky

naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ ```bash
docker port confident_zhukovsky ```

89/tcp -> 0.0.0.0:5000


`docker wait`

Block until one or more containers stop, then print their exit codes

```bash docker wait confident_zhukovsky
```
in other tab

docker stop confident_zhukovsky 
confident_zhukovsky

then the ourput is 

docker wait confident_zhukovsky 
137

```bash
docker rm`
```
Remove one or more containers using docker rm


docker run -d nginx

8326151018c709628fab93ce56941bd1a03628367e5009166e52d194c7c8ed77

docker stop 8326151018c7
8326151018c7

```bash
docker rm 8326151018c7
```
8326151018c7

`docker attach`

docker attach to attach our terminal's standard input, output, and error to a running container using the container's ID or name.

docker run -d nginx

a7746214a2592dfd9841dd7e91346fbdb0e4273d9ffa1ceeac98d0b1d8454ad0

docker ps

CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS     NAMES
a7746214a259   nginx     "/docker-entrypoint.…"   31 seconds ago   Up 29 seconds   80/tcp    eager_bartik


```bash
docker attach a7746214a259
```
^C2024/01/16 11:26:54 [notice] 1#1: signal 2 (SIGINT) received, exiting
2024/01/16 11:26:54 [notice] 32#32: exiting
2024/01/16 11:26:54 [notice] 29#29: exiting
2024/01/16 11:26:54 [notice] 30#30: exiting
2024/01/16 11:26:54 [notice] 31#31: exiting
2024/01/16 11:26:54 [notice] 33#33: exiting
2024/01/16 11:26:54 [notice] 34#34: exiting
2024/01/16 11:26:54 [notice] 32#32: exit
2024/01/16 11:26:54 [notice] 31#31: exit
2024/01/16 11:26:54 [notice] 34#34: exit
2024/01/16 11:26:54 [notice] 30#30: exit
2024/01/16 11:26:54 [notice] 33#33: exit
2024/01/16 11:26:54 [notice] 29#29: exit
2024/01/16 11:26:54 [notice] 36#36: exiting
2024/01/16 11:26:54 [notice] 35#35: exiting
2024/01/16 11:26:54 [notice] 36#36: exit
2024/01/16 11:26:54 [notice] 35#35: exit
2024/01/16 11:26:54 [notice] 1#1: signal 2 (SIGINT) received, exiting
2024/01/16 11:26:54 [notice] 1#1: signal 17 (SIGCHLD) received from 35
2024/01/16 11:26:54 [notice] 1#1: worker process 35 exited with code 0
2024/01/16 11:26:54 [notice] 1#1: signal 29 (SIGIO) received
2024/01/16 11:26:54 [notice] 1#1: signal 17 (SIGCHLD) received from 30
2024/01/16 11:26:54 [notice] 1#1: worker process 30 exited with code 0
2024/01/16 11:26:54 [notice] 1#1: signal 29 (SIGIO) received
2024/01/16 11:26:54 [notice] 1#1: signal 17 (SIGCHLD) received from 36
2024/01/16 11:26:54 [notice] 1#1: worker process 36 exited with code 0
2024/01/16 11:26:54 [notice] 1#1: signal 29 (SIGIO) received
2024/01/16 11:26:54 [notice] 1#1: signal 17 (SIGCHLD) received from 32
2024/01/16 11:26:54 [notice] 1#1: worker process 32 exited with code 0
2024/01/16 11:26:54 [notice] 1#1: worker process 34 exited with code 0
2024/01/16 11:26:54 [notice] 1#1: signal 29 (SIGIO) received
2024/01/16 11:26:54 [notice] 1#1: signal 17 (SIGCHLD) received from 34
2024/01/16 11:26:54 [notice] 1#1: signal 17 (SIGCHLD) received from 29
2024/01/16 11:26:54 [notice] 1#1: worker process 29 exited with code 0
2024/01/16 11:26:54 [notice] 1#1: worker process 33 exited with code 0
2024/01/16 11:26:54 [notice] 1#1: signal 17 (SIGCHLD) received from 33
2024/01/16 11:26:54 [notice] 1#1: worker process 31 exited with code 0
2024/01/16 11:26:54 [notice] 1#1: exit
naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ 



`docker cp`

CP command is used for cp from local to container or container to local.

touch copy_test.conf

naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ 

```bash
docker cp copy_test.conf 818d1bb178a7:/etc/nginx/conf.d
```
Successfully copied 1.54kB to 818d1bb178a7:/etc/nginx/conf.d

naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ 

```bash
docker exec 818d1bb178a7 ls /etc/nginx/conf.d
```
copy_test.conf
custom.conf
default.conf

This command is used for cp from container to host

```bash
docker cp 818d1bb178a7:/etc/nginx/conf.d/default.conf .
```
Successfully copied 3.07kB to /home/naeem/Downloads/DevOps Dice/Dice-Assignment1-Part2/.

naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ ls
copy_test.conf  custom.conf  default.conf  README.md

**Step 4: Document your results in README.md**

In this, I compile all the commands with output in README.md file.



**Step 5:Push the codebase for the sample application to your GitHub repository create a new one for this part**

```bash
git status
```
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	copy_test.conf
	custom.conf
	default.conf

no changes added to commit (use "git add" and/or "git commit -a")

```bash
git add . 
```
naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ 
```bash 
git commit -m "Compile all the commands in README.md
```
[main 8990a32] Compile all the commands in README.md
 4 files changed, 561 insertions(+)
 create mode 100644 copy_test.conf
 create mode 100644 custom.conf
 create mode 100644 default.conf

naeem@naeempc:~/Downloads/DevOps Dice/Dice-Assignment1-Part2$ 
```bash
git push origin main 
```
Username for 'https://github.com': itsnaeem
Password for 'https://itsnaeem@github.com': 
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 5.67 KiB | 5.67 MiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Itsnaeem/Dice-Assignment1-Part2.git
   200074a..8990a32  main -> main


## End of Part2 Assignment1

END of Part 2 Assignment 1.
