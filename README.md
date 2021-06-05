Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

![image](https://user-images.githubusercontent.com/78322958/120876818-a3377480-c578-11eb-86ce-b0fea54ca8b2.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

~/Elk_Project-1/Ansible

This document contains the following details:

* Description of the Topology
* Access Policies
* ELK Configuration
* Beats in Use
* Machines Being Monitored
* How to Use the Ansible Build
* Description of the Topology
* The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting attacks to the network. If a server becomes unavailable, or is down for updates, services can still continue. The advantage to using a jumpbox is that only it can access the Virtual Network using SSH.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

Filebeat monitors the log files or locations specified, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
Metricbeat is an extremely easy-to-use, efficient and reliable metric shipper for monitoring your system and the processes running on it. The configuration details of each machine may be found below.

The configuration details of each machine may be found below. 

 Name	    Function	                IP Address	                Operating System
Jump Box    Gateway         Public: 52.149.183.45 Private: 10.0.0.4          Linux
Web-1       Server          Public:N/A -- Private: 10.0.0.7                  Linux
Web-2       Server          Public:N/A -- Private: 10.0.0.8                  Linux
ELKSrvr     Monitoring      Public: 157.56.161.184 Private: 10.1.0.4         Linux

Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 

* 5601 Kibana Port
 
Machines within the network, including the ELK Server, can only be accessed by the Jump Box Provisioner (IP 52.149.183.45).

A summary of the access policies in place can be found in the table below.

Name       Publicly Accessible	Allowed IP Address
Jump Box          Yes              66.69.206.54
Web-1             No                 10.0.0.4
Web-2             No                 10.0.0.4
ELK-Server        No                 10.0.0.4

Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it simplifies the process and prevents any easily overlooked vulnerabilties.

The playbook implements the following tasks:

* Installs docker.io
* Installs python3-pip
* Increase virtual memory
* Install docker via pip
* Download and install a docker ELK container - starts docker and sets up the ports being utilized.

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/78322958/120878272-e0a00000-c580-11eb-9b1c-44fcf879878b.png)


Target Machines & Beats
This ELK server is configured to monitor the following machines:

* Web-1 - 10.0.0.7

* Web-2 - 10.0.0.8

We have installed the following Beats on these machines:

* Filebeat
* Metricbeat

* Web-1 - 10.0.0.7
* Web-2 - 10.0.0.8
* ELK-Server - 10.1.0.4

These Beats allow us to collect the following information from each machine:

* Filebeat collects data from logs lists it out in monitoring clusters. 
* Metricbeat collects metrics and statistics and lists them in the output specified, i.e. Elasticsearch or Logstash.

Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the Install-ELK.yml file to the Ansible directory.
Update the hosts file to include webserver and ELK.
Run the playbook, and navigate to the Kibana URL specific to your IP to check that the installation worked as expected.
