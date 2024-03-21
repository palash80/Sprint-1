## Bit bucket Application Template

### INTRODUCTION

 BitBucket is a cloud-based service that helps developers store and manage their code, as well as track and control the changes to their code. BitBucket provides a cloud-based Git repository hosting service. Its interface is user-friendly enough so even novice coders can take advantage of Git. We generally require a bit more technical knowledge and use of the command line to use Git alone. Additionally, BitBuckets provides a variety of services like it gives teams to collaborate and create projects, test and deploy the code.


| Author         | Created on | Version | Last updated by  | Last edited on |
|----------------|------------|---------|------------------|----------------|
| Palash Kamble  | 20 03 2023 | 8.0     | Palash Kamble    | 09 Feb 2023    |


## Purpose of Application

> Bitbucket is a cloud-based service that helps developers manage their code, as well as track and control changes to it. It provides a user-friendly Git repository hosting service, allowing teams to collaborate and create projects, test, and deploy code.

> Before the advent of Bitbucket, developers might have used Git alone, which requires more technical knowledge and the use of command-line interfaces. Bitbucket offers a more accessible solution, enabling even novice coders to work with Git.

**Bitbucket solves several problems faced by developers, including:**

**Remote code storage and management:** Bitbucket allows users to store their code securely in the cloud, freeing them from the need to rely on local storage and offering a convenient solution for remote collaboration.
  
 **Collaboration and teamwork:** Bitbucket's interface enables better teamwork through its built-in collaboration tools, allowing teams to plan, track and execute projects efficiently.
  
 **Version control and tracking:** Bitbucket helps developers track changes to their code and manage revisions, enabling better collaboration and more efficient development.
  
 **Integration with other tools:** Bitbucket can be integrated with popular tools like Jira, Trello, and Bamboo, further streamlining development workflows and enhancing communication among teams.



### Pre-requisites

**Java**
Note- Java version should be 8,11,13




### System Requirements

| Hardware Specifications | Minimum Recommendation |
|--------------------------|------------------------|
| **Processor**            | Any modern processor capable of running a web browser smoothly, such as an Intel Core i3 or equivalent. |
| **RAM**                  | At least 1GB of RAM to ensure smooth browsing experience and basic functionality. |
| **Storage**              | No specific local storage requirements, as Bitbucket is a cloud-based service. However, ensure you have enough space for browser cache and temporary files. |
| **Network**              | A stable internet connection with at least 1 Mbps download and upload speed for seamless access to Bitbucket's web interface and repository interactions. |



### Important Ports
*Note that Bitbucket Server's default ports are 7999 for SSH & 7990 for HTTP;

| Port | Service |
|------|---------|
| 7999 | SSH     |
| 7990 | HTTP    |




**Installation of bit bucket OS (ubuntu)**


Steps;

1. **Link for Download tar file**
(https://confluence.atlassian.com/bitbucketserver087/install-bitbucket-server-on-linux-1209861839.html)
2. Download tar file according to the release.
3. Extract the tar file "tar -xvf atlassian-bitbucket-8.19.0.tar.gz"
4. cd atlassian-bitbucket-8.19.0
5. Change the path where the vcs  data want to stored by using  editor to the file "bin/set-bitbucket-home.sh"
6. Start the service of bit bucket "./start-bitbucket.sh" 
7. Check it is working or not by hitting localhost:7990





