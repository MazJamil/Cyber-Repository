## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Cyber-Repository/Project1-ELK/README/Images/Network_Diagram.png


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

Cyber-Repository/Project1-ELK/README/Ansible/filebeat.yml


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

What aspect of security do load balancers protect? What is the advantage of a jump box?
The aspect of security that load balancers protect is by altering incident traffic from DDOS attacks. The advantage of a jumpbox is to, via a single node, provide access to the user where it can be monitored and secured.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system network

What does Filebeat watch for?
Filebeat monitors the locations you specify or the log files

What does Metricbeat record?
Metricbeat records the statistics and “metrics” from the os as well as services that are running on the server

The configuration details of each machine may be found below.


|    Name    | Function | IP Address | Operating System |
|:----------:|----------|:----------:|:----------------:|
| Jump-Box   | Gateway  | 10.1.0.4   | Linux            |
| Web-1      | Server   | 10.1.0.5   | Linux            |
| Web-2      | Server   | 10.1.0.6   | Linux            |
| Web-3 DVWA | Server   | 10.1.0.9   | Linux            |



### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
20.85.238.23

Machines within the network can only be accessed by Jumpbox
10.1.0.4

A summary of the access policies in place can be found in the table below.

|    Name    | Publicly Accessible | Allowed IP Addresses |
|:----------:|:-------------------:|:--------------------:|
| Jump-Box   | Yes                 | 20.85.238.23         |
| Web-1      | No                  | 10.1.0.4             |
| Web-2      | No                  | 10.1.0.4             |
| Web-3 DVWA | No                  | 10.1.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the processes of configuring additional machines gets simplified.
What is the main advantage of automating configuration with Ansible?
The main advantage of Ansible is to simplify the processes and configuration so to rely on automation

The playbook implements the following tasks:

-	Docker – via containers Installation
-	Python3-pip Installation
-	Docker Python Module Installation
-	Virtual Memory Increase
-	Download and initiate Docker ELK containers accordingly 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Cyber-Repository/Project1-ELK/README/Images/docker-ps.png


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-	Web 1 – 10.1.0.5
-	Web 2 – 10.1.0.6
-	Web 3 DVWA – 10.1.0.9

We have installed the following Beats on these machines:

Filebeat
Metricbeat
These Beats allow us to collect the following information from each machine:

In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat examines the logs files and location which are used to see changes that the log files have received.  Metricbeat documents and operations running on the server which can be viewed to see CPU usage at a given time on the webserver. 

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yml.config file to /etc/ansible
- Update the /etc/ansible/hosts file to include the IP group of hosts machines
- Run the playbook, and navigate to ELK Server/kibana to check that the installation worked as expected.

Which file is the playbook? install-elk.yml 

Where do you copy it? /etc/ansible

Which file do you update to make Ansible run the playbook on a specific machine? Hosts file 

How do I specify which machine to install the ELK server on versus which to install Filebeat on? The host file is manipulated to specify the allocated IP addresses to install. 

Which URL do you navigate to in order to check that the ELK server is running? VM IP Address:5601/app/kibana

