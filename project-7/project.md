# **DEVOPS TOOLING WEBSITE SOLUTION**

In this project you will implement a solution that consists of following components:

* Infrastructure: AWS

* Webserver Linux: Red Hat Enterprise Linux 8

* Database Server: Ubuntu 20.04 + MySQL

* Storage Server: Red Hat Enterprise Linux 8 + NFS Server

* Programming Language: PHP

* Code Repository: Github

![Architecture](./images/achitecture-diagram.png)

## STEP 1 – PREPARE NFS SERVER

1. Spin up a new EC2 instance with RHEL Linux 9 Operating System.

![nfs-server](./images/nfs-server.png)

2. Create and Add  EBS volumes to the EC2 instance.

![attaching-volume](images/attaching-volume-to-instance.png)

3. Open up the linux terminal to begin configuration.
   
4. Use **lsblk** command to inspect what block devices are attached to the server. 

```
$ lsblk
```

![attached-volume](./images/attached-volumes-server.png)

5. Use **gdisk** utility to create a single partition on each of the 3 disks

```
$ sudo gdisk /dev/xvdf
```
![volume-partition](./images/volume-partition.png)

6. Install **lvm2** package using sudo yum install lvm2. Run **sudo lvmdiskscan** command to check for available partitions.

```
$ sudo lvmdiskscan 