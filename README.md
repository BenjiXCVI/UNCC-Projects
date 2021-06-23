# UNCC-Projects
Project done during cybersecurity bootcamp

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1eueOlFNS7XU2rjTFCIoVPatgYy4bCnk1/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient , in addition to restricting downtime to the network.
What aspect of security do load balancers protect? What is the advantage of a jump box?
The load balancer protects from possible ddos attacks and helps manage traffic. The main advantage of the jump box is the secure shell protocol (SSH) which allows secure access between all the virtual machines on the network

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
Filebeat watches for system log events on the machine
Metricbeats is used to monitor statistics of the operating system and services running on the machine








The configuration details of each machine may be found below.

| NAME       	| Function 	| IP Addresses  	|
|------------	|----------	|---------------	|
| JUMP-BOX   	| Gateway  	| 96.36.131.54  	|
| WEB-1      	| DVWA     	| 10.0.0.5      	|
| WEB-2      	| DVWA     	| 10.0.0.6      	|
| WEB-3      	| DVWA     	| 10.0.0.7      	|
| ELK Server 	| Monitor  	| 52.148.189.48 	|








### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresse:
96.36.131.54

Machines within the network can only be accessed by the jump-box provisioner.
The jumpbox machine is the only vm allowed to ssh into the elk server from IP 52.154.26.228

A summary of the access policies in place can be found in the table below.
| NAME       	| Publicly Accessible 	| Allowed IP Addresses 	|   	|
|------------	|---------------------	|----------------------	|---	|
| JUMP-BOX   	| No                  	| 96.36.131.54         	|   	|
| WEB-1      	| No                  	| 52.154.26.228        	|   	|
| WEB-2      	| No                  	| 52.154.26.228        	|   	|
| WEB-3      	| No                  	| 52.154.26.228        	|   	|
| ELK Server 	| no                  	| 52.154.26.228        	|   	|


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for a quick deployment of the containers. All of the configuration was set up and run through a playbook allowing secure and consistent connection.

The playbook implements the following tasks:
Step one was to install docker .io followed by
Install pip3 to manage software packages
Download and launch a docker elk container with three published ports (5601,9200,5044)

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 VM ip: 10.0.0.5
Web-2 VM ip: 10.0.0.6
Web-3 VM ip: 10.0.0.7

I have installed the following Beats on these machines:
Filebeats on two of my web virtual machines along with winlogbeat


These Beats allow us to collect the following information from each machine:
Winlogbeat allows me to  monitor event logs from security events , and system events and forwards data to elasticsearch also filtering the data based on user configuration 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-configuration.yml file to the filebeat-playbook.yml.
- Update the ansible host file to include the correct IP for the virtual machine you want to run the playbook on
- Run the playbook, and navigate to kibana using the elk ip to check that the installation worked as expected.
