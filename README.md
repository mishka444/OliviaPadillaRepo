# OliviaPadillaRepo
ElkStack Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Elk-Stack Diagram](https://github.com/mishka444/OliviaPadillaRepo/blob/main/Diagram/ELK-Stack%20Diagram.drawio%20(1).png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat. The links to the files provided are txt because I was unable to access my Azure account after day three. Therefore, some of this project will be writted and some will have screenshots.

 [Elk-Stack Playbook](https://github.com/mishka444/OliviaPadillaRepo/blob/main/Ansible/Elk-PlayBook.yml)
 
 [FileBeat Playbook](https://github.com/mishka444/OliviaPadillaRepo/blob/main/Ansible/FileBeatPlaybook.yml)
 
 [Metric Playbook](https://github.com/mishka444/OliviaPadillaRepo/blob/main/Ansible/MetricPlaybook.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly obtainable, in addition to restricting access to the network.
Load balancers are there to ensure that an application is accessible while also restricting access to the virtual network. Load balancers also allow for availibilty in the virtual environment by distributing specific information to the web servers. The jump box provides a more effective and quick way to manage multiple systems. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the event logs and system metrics.
FileBeat watches and montiros for specific log files in the system.
Metricbeat records metrics and statistics and sends them to any output you choose.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.1   | Linux            |
| Web-1    | Server     | 10.0.0.8   | Linux            |
| Web-2    | Server     | 10.0.0.7   | Linux            |
| ELK      | Log Server | 10.0.1.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addressesses:
- Personal Host IP Addresses

Machines within the network can only be accessed by the JumpBox. The Jump Box is able to connect to our ELK VM by using SSH through port 22. 
The machine was accessed through the JumpBox with a personal IP

A summary of the access policies in place can be found in the table below.

![](https://github.com/mishka444/OliviaPadillaRepo/blob/main/Images/Screen%20Shot%202021-12-11%20at%203.43.09%20PM.png)
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the system installation could be done more efficiently.

The playbook implements the following tasks:

![](https://github.com/mishka444/OliviaPadillaRepo/blob/main/Ansible/Ansible%20Images/Elk%20SC.png)

How to Install ELK

- Start your JumpBox Virtual Machine and then create a new Virtual Machine titled ELK
- Connect to your RedTeam resource groups and networks 
- Open your terminal and enter your Sudo commands to open the container
- An SSH key will appear which will allow you to install your ELK Machine
- Run playbook and navigate to Kibana

Was Unable to get screenshot at this point due to my Azure locking me out, so instead I will explain the process. 

You should get a container ID from the command "/bn/sh -c /bin/bash" that will signal that your Elk is up and running.

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.0.0.8)
- Web-2 (10.0.0.7)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat is used for forwarding an centralizing log data. It also is used to monitor the logfiles and the locations you tell it to.
- Metricbeat is used to measure the metrics and statistic from your OS and from the services running them. They send these stats to your specified output

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
For ELK VM Configuration:

Copy the Ansible ELK Installation and VM Configuration
Run the playbook using this command : ansible-playbook install-elk.yml

For FileBeat

Download Filebeat playbook usng this command:
curl -L -O https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/files/filebeat-config.yml

- Copy the '/etc/ansible/files/filebeat-config.yml' file to '/etc/filebeat/filebeat-playbook.yml'

- Update the filebeat-playbook.yml file to include installer

curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.6.1-amd64.deb

- Update the filebeat-config.yml file root@c1e0a059c0b0:/etc/ansible/files# nano filebeat-config.yml

![](https://github.com/mishka444/OliviaPadillaRepo/blob/main/Ansible/Ansible%20Images/FileBeat%20SC.png)


For MetricBeat:

- Download Metricbeat playbook using this command: 
curl -L -O https://gist.githubusercontent.com/slape/58541585cc1886d2e26cd8be557ce04c/raw/0ce2c7e744c54513616966affb5e9d96f5e12f73/metricbeat > /etc/ansible/files/metricbeat-config.yml

- Copy the /etc/ansible/files/metricbeat file to /etc/metricbeat/metricbeat-playbook.yml

- Update the filebeat-playbook.yml file to include installer
curl -L -O https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.6.1-amd64.deb

![](https://github.com/mishka444/OliviaPadillaRepo/blob/main/Ansible/Ansible%20Images/MetricBeat%20SC.png)


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
