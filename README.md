# ELK-PROJECT
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/Ctradke/ELK-PROJECT/blob/main/server%20diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.

  

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting traffic to the network.
The load blancer will help stop ddos attatcks by shifting the traffic, the jumbox provides a controlled access point to the servers._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
-File beat watcges fir log files and collects log events

-Metric beat records statstical data from the machines and servives that are opertion on the server 

The configuration details of each machine may be found below.


| Name      | Function  | IP Address | Operating System |
|-----------|-----------|------------|------------------|
| Jump Box  | Gateway   | 10.0.0.4   |Linux             |
| VM1       |DOCKER-DVWA| 10.0.0.5   |Linux             |
| VM2       |DOCKER-DVWA| 10.0.0.6   |Linux             |
| VM3       |DOCKER-DVWA| 10.0.0.7   |Linux             |
| ELK-SERVER|ELK        | 10.0.0.8   |Linux             |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-68.47.62.202

Machines within the network can only be accessed by SSH.

- The only machine that can acces the ELk Server (10.0.0.8) is through the Jump box (10.0.0.4)

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses |
|---------- |---------------------|----------------------|
| Jump Box  | No                  |68.47.62.202          |
| VM 1      | No                  | 10.0.0.4             |
| VM 2      | No                  | 10.0.0.4             |
| VM 3      | No                  | 10.0.0.4             |
| ELK-SERVER| No                  | 10.0.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The advantages of the automation through ansible is the ease if use and through the use of playbooks you are able to configure multiple machines with one command.

The playbook implements the following tasks:


-First we will need to install docker .io, pip 3 and the docker module

-Next we will need to increase the virtual memory in order to run the elk server on the virtual machine

- Then will need to use the sysctl model

- last is to download and lauch the docker container for elk server 


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/Ctradke/ELK-PROJECT/blob/main/docker%20ps.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- VM 1 at 10.0.0.5 
- VM 2 at 10.0.0.6
- VM 3 at 10.0.0.7

We have installed the following Beats on these machines:
- File Beat and Metric Beat 

These Beats allow us to collect the following information from each machine:

- File beat is for forwarding and centralizing log data, it monitors log files or locations , collects log events and forwards them to eight Elasticsearch or Logstash for indexing
-Metric beat collects metrics from the operating system and services running on the server, takes the metrics and stats colleced and outputs them where you have specified.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yml file to VMs_.
- Update the host file to include... ip address of the elk server
- Run the playbook, and navigate to http://[Elk_VM_Public_IP]:5601/app/kibana to check that the installation worked as expected.



