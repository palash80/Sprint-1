
## Purpose

The Employee REST API, developed in Golang, manages all employee-related transactions within the [OT-Microservices](https://github.com/OT-MICROSERVICES) repository. It boasts platform independence, enabling deployment across diverse environments effortlessly.

### Supported Features for the Application:

* ScyllaDB as database for storing information.
* Redis as a cache management 
* REST API for web transactions

### Key Components 
 

| Tool/Software | Usage  |
| ------------- | --------------------------------------------------------- | 
| `Spring boot` | A web framework based on Java, utilizing Tomcat as its web server.  | 
| `ScyllaDB`    | Serves as the primary database for storing all employee data. |
| `Redis`       | Functions as a cache manager to store cache responses.|
| `migrate`     | Facilitates database migration. |



### System Requirements

| System Requirement                |           Minimum                          |
|-----------------------------------|--------------------------------------------|
| Processor/Instance Type           |             Dual Core/t2.medium            | 
| RAM                               |               4GB                          |
| Disk Space                        |               20GB                         |            
| OS Required                       |             Ubuntu 20.04 LTS               |



### Important Ports

| Port | Description             |
|------|-------------------------|
| 22   | ssh                     |
| 8080 | Employee API port       |
| 9042 | ScyllaDB                |
| 6379 | Redis                   |


### Pre-requisites

The application's setup requirements are minimal, primarily necessitating only database connectivity. Although optional, the integration of Redis as a cache system can enhance performance, yet it is not.

For running the application, we need following things configured:

1. ScyllaDB
2. Redis
3. Java 17
4. Migrate



# Step-by-step installation 
## Step1: Install Dependencies required for software
### Install ScyllaDB

1. Install a repo file and add the ScyllaDB APT repository to your system.

   <tab><tab><pre><code>`sudo mkdir -p /etc/apt/keyrings`</code></pre>

![image](https://github.com/palash80/Sprint-1/assets/153359214/4a8adcba-bf07-405f-9edc-ed145a195a5c)

<tab><tab><pre><code>`sudo gpg --homedir /tmp --no-default-keyring --keyring /etc/apt/keyrings/scylladb.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys d0a112e067426ab2
`</code></pre>

![image](https://github.com/palash80/Sprint-1/assets/153359214/4a8adcba-bf07-405f-9edc-ed145a195a5c)

<tab><tab><pre><code>`sudo wget -O /etc/apt/sources.list.d/scylla.list http://downloads.scylladb.com/deb/debian/scylla-5.4.list
`</code></pre>

2. Install ScyllaDB packages

<tab><tab><pre><code>`sudo apt-get update`</code></pre>

<tab><tab><pre><code>`sudo apt-get install -y scylla
`</code></pre>


3. (Ubuntu only) Set Java 17

```shell
sudo apt-get update
sudo apt-get install -y openjdk-17-jre-headless
sudo update-java-alternatives --jre-headless -s java-1.17.0-openjdk-amd64
``` 


### Configure ScyllaDB

* Configure the following parameters in the /etc/scylla/scylla.yaml configuration file.

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

### Scylla Setup

* This script tunes system settings and determines optimal configurations.

  <tab><tab><pre><code>sudo scylla_setup</code></pre>

**NOTE**
* Read the requirenment carefully as per your need and select **YES**/**NO**


![image](https://github.com/palash80/Sprint-1/assets/153359214/be8202d7-a66e-4ed9-bdcc-d72157515968)

![image](https://github.com/palash80/Sprint-1/assets/153359214/30dade57-dca7-4b80-8a0d-871f0a2efe3b)

![image](https://github.com/palash80/Sprint-1/assets/153359214/05a23d15-cc38-4f5b-a0da-56f2280e2a95)

![image](https://github.com/palash80/Sprint-1/assets/153359214/571af304-5d12-41f7-9144-c3687469b88d)

 * Start Service of ScyllaDB

<tab><tab><pre><code>sudo systemctl start scylla-server</code></pre>


![image](https://github.com/palash80/Sprint-1/assets/153359214/42e6fd00-d6f6-4eed-bbf5-d833f4dab805)

* Check the service is running or not

![image](https://github.com/palash80/Sprint-1/assets/153359214/f393869e-e544-49b6-b93b-63df63ef04f3)


* login to scylla shell and play around the features


* Run cqlsh command

<tab><tab><pre><code>cqlsh IP</code></pre>

![image](https://github.com/palash80/Sprint-1/assets/153359214/ad8dc974-175b-4b84-b74f-d331aa503d66)


### Install Migrate


```shell
curl -s https://packagecloud.io/install/repositories/golang-migrate/migrate/script.deb.sh | sudo bash
sudo apt-get update
sudo apt-get install migrate
``` 

### Install JQ (JSON processor)

```shell
sudo apt install jq
``` 











