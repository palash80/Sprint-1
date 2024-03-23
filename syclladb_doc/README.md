
# ScyllaDB Installation


| Author         | Created on | Version | Last updated by  | Last edited on |
|----------------|------------|---------|------------------|----------------|
| Palash Kamble  | 23 /03/ 2024 | 1.0     | Palash Kamble    | 23 /03/2024  |

# Table of Contents



| Section                                      |
|----------------------------------------------|
|1. [Introduction](#introduction)                |
|2. [Important Ports](#important-ports)          |
|3. [Architecture](#architecture)                |
|4. [How to Setup/Install ScyllaDB](#how-to-setupinstall-scylladb) |
|5. [Configure ScyllaDB](#configure-scylladb)    |
|6. [Scylla Setup](#scylla-setup)                |
|7. [Conclusion](#conclusion)                    |
|8. [Contact](#contact)                          |



# Introduction

ScyllaDB is a highly scalable and performance-oriented distributed NoSQL database. It is based on the Apache Cassandra project and is designed to handle large volumes of data with low latency and high throughput. ScyllaDB is optimized for modern hardware architectures and utilizes a shared-nothing architecture to achieve horizontal scalability. It offers features such as tunable consistency levels, automatic data partitioning, and built-in fault tolerance mechanisms. ScyllaDB is widely used in various industries for applications requiring real-time data processing, high availability, and predictable performance.



## Key Features

| Key Feature        | Description                                               |
|--------------------|-----------------------------------------------------------|
| Highly Scalable    | Scales seamlessly to handle large volumes of data.        |
| Low Latency        | Provides fast data access with minimal delay.             |
| High Availability  | Ensures data is always accessible, minimizing downtime.   |
| Easy to Use        | Simple to deploy and manage, with user-friendly interfaces. |
| High Performance   | Optimized for speed and efficiency, delivering rapid data processing.|


### System Requirements

| System Requirements | Description               |
|---------------------|---------------------------|
| Operating System    | Ubuntu                    |
| RAM                 | 4 GB or higher            |
| Disk Space          | 10 GB or higher           |
| Processor           | 2 GHz dual-core processor or higher |



### Important Ports

| Important Ports | Description                             |
|-----------------|-----------------------------------------|
| 7199            | JMX monitoring port                     |
| 7000            | Inter-node communication                |
| 7001            | SSL inter-node communication            |
| 9042            | CQL native transport (client port)      |
| 9160            | Thrift client API                       |
| 7199            | JMX monitoring port                     |


### Architecture 

![Screenshot from 2024-03-23 12-48-31](https://github.com/palash80/Sprint-1/assets/153359214/a9ed2d51-a9d4-4b1e-a35b-cf40bc3a25ea)


### How to Setup/Install ScyllaDB

**Step-1**

>Install a repo file and add the ScyllaDB APT repository to your system.

<tab><tab><pre><code>`sudo mkdir -p /etc/apt/keyrings`</code></pre>


![image](https://github.com/palash80/Sprint-1/assets/153359214/4a8adcba-bf07-405f-9edc-ed145a195a5c)

**Step-2**

>Import gpg key


<tab><tab><pre><code>`sudo gpg --homedir /tmp --no-default-keyring --keyring /etc/apt/keyrings/scylladb.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys d0a112e067426ab2
`</code></pre>


![image](https://github.com/palash80/Sprint-1/assets/153359214/4a8adcba-bf07-405f-9edc-ed145a195a5c)

**Step-3**

>Download ScyllaDB APT repository configuration file

<tab><tab><pre><code>`sudo wget -O /etc/apt/sources.list.d/scylla.list http://downloads.scylladb.com/deb/debian/scylla-5.4.list
`</code></pre>

**Step-4**


Install ScyllaDB packages

>Update the package list

<tab><tab><pre><code>`sudo apt-get update`</code></pre>

<tab><tab><pre><code>`sudo apt-get install -y scylla
`</code></pre>


**Step-5**

(Ubuntu only) Set Java 17

>Update the package list
<tab><tab><pre><code>`sudo apt-get update
`</code></pre>


>Install java

<tab><tab><pre><code>sudo apt-get install -y openjdk-17-jre-headless`</code></pre>

>Set the java version
<tab><tab><pre><code>sudo update-java-alternatives --jre-headless -s java-1.17.0-openjdk-amd64
`</code></pre>


**Step-6**

### Configure ScyllaDB

<tab><tab><pre><code>vi /etc/scylla/scylla.yml`</code></pre>


![image](https://github.com/palash80/Sprint-1/assets/153359214/205761c2-1203-4081-bec1-ffcd62e3782b)

![image](https://github.com/palash80/Sprint-1/assets/153359214/03b80294-f754-4e1c-897b-351e057dda9c)

![image](https://github.com/palash80/Sprint-1/assets/153359214/6e2b5690-1ce5-4b83-ac6a-2567bf3628a6)


**NOTE**
In above screenshot We have to make the changes (Private IP) in three terms
1. Listen_address
2. rpc_adress
3. seeds

**seeds** : This is the PRIVATE IP address that Scylla will use to connect to other Scylla nodes in the cluster. 
  Seed nodes are used during startup to bootstrap the gossip process and join the cluster

**listen_address**: This is the PRIVATE IP address that Scylla will use to connect to other Scylla nodes in the cluster. In this case, it's set to 'localhost,' indicating that it will listen for connections on the local machine.

**rpc_address**: This is the PRIVATE IP address of the interface for client connections, such as Thrift and CQL. Similar to listen_address, it is set to 'localhost' in this configuration.

## Scylla Setup

**Step-7**

>This script tunes system settings and determines optimal configurations.

<tab><tab><pre><code>sudo scylla_setup</code></pre>



**NOTE**
> Read the requirenment carefully as per your need and select **YES**/**NO**


![image](https://github.com/palash80/Sprint-1/assets/153359214/be8202d7-a66e-4ed9-bdcc-d72157515968)

![image](https://github.com/palash80/Sprint-1/assets/153359214/30dade57-dca7-4b80-8a0d-871f0a2efe3b)

![image](https://github.com/palash80/Sprint-1/assets/153359214/05a23d15-cc38-4f5b-a0da-56f2280e2a95)

![image](https://github.com/palash80/Sprint-1/assets/153359214/571af304-5d12-41f7-9144-c3687469b88d)

**Step-8**

>Start Service of ScyllaDB

<tab><tab><pre><code>sudo systemctl start scylla-server</code></pre>

sudo systemctl start scyllaserver

![image](https://github.com/palash80/Sprint-1/assets/153359214/42e6fd00-d6f6-4eed-bbf5-d833f4dab805)

**Step-9**

>Check the service is running or not

![image](https://github.com/palash80/Sprint-1/assets/153359214/f393869e-e544-49b6-b93b-63df63ef04f3)

**Step-10**

>login to scylla shell and play around the features


>Run cqlsh command

<tab><tab><pre><code>cqlsh IP</code></pre>

![image](https://github.com/palash80/Sprint-1/assets/153359214/ad8dc974-175b-4b84-b74f-d331aa503d66)

## Conclusion

Upon successful installation of ScyllaDB, ensure that the system requirements are met, including proper configuration of the operating system, hardware, and network settings. Verify that the installation method aligns with your deployment strategy, whether it be package installation or tarball installation. Confirm cluster topology and configuration, ensuring adequate replication and fault tolerance. Finally, test data access and query performance to ensure seamless integration with your application and optimal utilization of ScyllaDB's capabilities.

## Contact

| Name          | Email                    |
|---------------|------------------------- |
| Palash Kamble | palash.Kamble@opstree.com|



## Refrence link Doc
(https://opensource.docs.scylladb.com/stable/getting-started/system-configuration.html#system-configuration-scripts)
























