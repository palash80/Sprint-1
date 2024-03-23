
# ScyllaDB Installation


# Key Features

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



## Important Ports

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


## How to Setup/Install ScyllaDB

**Step-1**

>Install a repo file and add the ScyllaDB APT repository to your system.

sudo mkdir -p /etc/apt/keyrings

![image](https://github.com/palash80/Sprint-1/assets/153359214/4a8adcba-bf07-405f-9edc-ed145a195a5c)

**Step-2**

sudo gpg --homedir /tmp --no-default-keyring --keyring /etc/apt/keyrings/scylladb.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys d0a112e067426ab2

![image](https://github.com/palash80/Sprint-1/assets/153359214/4a8adcba-bf07-405f-9edc-ed145a195a5c)

**Step-3**

sudo wget -O /etc/apt/sources.list.d/scylla.list http://downloads.scylladb.com/deb/debian/scylla-5.4.list

**Step-4**

Install ScyllaDB packages

sudo apt-get update
sudo apt-get install -y scylla

**Step-5**

(Ubuntu only) Set Java 17

sudo apt-get update
sudo apt-get install -y openjdk-17-jre-headless
sudo update-java-alternatives --jre-headless -s java-1.17.0-openjdk-amd64

**Step-6**

### Configure ScyllaDB

vi /etc/scylla/scylla.yml

![image](https://github.com/palash80/Sprint-1/assets/153359214/205761c2-1203-4081-bec1-ffcd62e3782b)

![image](https://github.com/palash80/Sprint-1/assets/153359214/03b80294-f754-4e1c-897b-351e057dda9c)

![image](https://github.com/palash80/Sprint-1/assets/153359214/6e2b5690-1ce5-4b83-ac6a-2567bf3628a6)


**NOTE**
In above screenshot We have to make the changes (Private IP) in three terms
1. Listen
2. rpc
3. seeds

## Scylla Setup

**Step-7**

sudo scylla_setup

**NOTE**
> Read the requirenment carefully as per your need and select **YES**/**NO**


![image](https://github.com/palash80/Sprint-1/assets/153359214/be8202d7-a66e-4ed9-bdcc-d72157515968)

![image](https://github.com/palash80/Sprint-1/assets/153359214/30dade57-dca7-4b80-8a0d-871f0a2efe3b)

![image](https://github.com/palash80/Sprint-1/assets/153359214/05a23d15-cc38-4f5b-a0da-56f2280e2a95)

![image](https://github.com/palash80/Sprint-1/assets/153359214/571af304-5d12-41f7-9144-c3687469b88d)

**Step-8**

Start Service of ScyllaDB

sudo systemctl start scylla-server

![image](https://github.com/palash80/Sprint-1/assets/153359214/42e6fd00-d6f6-4eed-bbf5-d833f4dab805)

**Step-9**

Check the service is running or not

![image](https://github.com/palash80/Sprint-1/assets/153359214/f393869e-e544-49b6-b93b-63df63ef04f3)

**Step**

login to scylla shell and play around the features

Run cqlsh command

cqlsh IP

![image](https://github.com/palash80/Sprint-1/assets/153359214/ad8dc974-175b-4b84-b74f-d331aa503d66)

## Conclusion

Upon successful installation of ScyllaDB, ensure that the system requirements are met, including proper configuration of the operating system, hardware, and network settings. Verify that the installation method aligns with your deployment strategy, whether it be package installation or tarball installation. Confirm cluster topology and configuration, ensuring adequate replication and fault tolerance. Finally, test data access and query performance to ensure seamless integration with your application and optimal utilization of ScyllaDB's capabilities.

## Contact

| Name          | Email                    |
|---------------|------------------------- |
| Palash Kamble | palash.Kamble@opstree.com|



## Refrence link Doc
(https://opensource.docs.scylladb.com/stable/getting-started/system-configuration.html#system-configuration-scripts)
























