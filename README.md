# ELK-Stack-Project
 UCB Cybersecurity Projects

Project 1 - ELK Stack Project

# Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/Azure-Diagram.png)![Untitled Diagram drawio (1)](https://user-images.githubusercontent.com/90795727/160530510-ceef74a6-91c8-4e1f-845e-81b7bf932277.png)



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

#Playbook Files

install-elk.yml
- Install Docker
- Install Python3-pip
- Install Docker Python Module
- Change Memory Usage to 262144
- Download and Launch Elf Container
- Enable Sercive Docker on Boot

install filebeat-playbook.yml
- Install and Launch Filebeat
- Downlaod Filebeat deb
- Drop in filebeat.yml
- Enable and Configure System Module
- Setup filebeat
- Start filebeat service
- Enable service filebeat on Boot

install metric-playbook.yml
- Download metricbeat
- Install metricbeat
- Drop in metricbeat
- Enable and configure docker module for metricbeat
- Setup metricbeat
- Start metricbeat
- enable service metricbeat on Boot

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


## Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible, in addition to restricting excessive traffic to the network.

- Load balancers protect accessibility of the network from attacks such as DDos attacks. The advantage of a jump box is protection of the host computer. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.

- Filebeat is a shipper for forwarding and centralizing log data. It is used to watch log files or specified locations which then collect log event and forwards them to Elasticsearch or Logstash.

- Metric beat takes the metric and statistics that it collects and ships them to the output that is specified. It records metrics from the system and services running on the server. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function   | IP Address | Operating System |
|------------|------------|------------|------------------|
| Jump Box   | Gateway    | 10.0.0.4   | Linux            |
| Web-1      | DVWA       | 10.0.0.5   | Linux            |
| Web-2      | DVWA       | 10.0.0.6   | Linux            |
| Web-3      | DVWA       | 10.0.0.7   | Linux            |
| ELK-Server | ELK STACKS | 10.1.0.4   | Linux            |

## Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 108.75.76.247

Machines within the network can only be accessed by JumpBoxProvisioner machine.

The machine that is allowed access to the ELF VM is the JumpBoxProvisioner. Its IP address is 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| Jump Box   | No                  | 108.75.76.247        |
| Web-1      | No                  | 10.0.0.4             |
| Web-2      | No                  | 10.0.0.4             |
| Web-3      | No                  | 10.0.0.4             |
| ELK-Server | No                  | 108.75.76.247        |

## Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- The main advantage of automating configuration with Ansible is that you can configure multiple machines all at once without having to go into each one individually. 

The playbook implements the following tasks:

- Install Docker
- Install Python3-pip
- Install Docker Python Module
- Change Memory Usage to 262144
- Download and Launch Elf Container
- Enable Sercive Docker on Boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)![docker_ps_output](https://user-images.githubusercontent.com/90795727/160270994-443823a2-d443-4aac-823f-0b99910f0ad2.png)


## Target Machines & Beats
This ELK server is configured to monitor the following machines:

- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:

- filebeat
- metricbeat

These Beats allow us to collect the following information from each machine:

- Filebeat is a shipper for forwarding and centralizing log data. It is used to watch log files or specified locations which then collect log event and forwards them to Elasticsearch or Logstash.

- Metric beat takes the metric and statistics that it collects and ships them to the output that is specified. It records metrics from the system and services running on the server. Some of the metrics include cpu, memory, network, etc. 

## Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to JumpBoxProvisioner machine.
- Update the configuration file to include the host file. 
- Run the playbook, and navigate to the ELK-Server to check that the installation worked as expected.

The playbook files are the files that include .yml extension. It is copied into /etc/ansible/roles.

You have to update the hosts file to run the playbook on a specific machine and to specify whcih machine to install the ELK server on versus which to install Filebeat on. 

You have to run the playbook and the navigate to Kibana to check the installation worked properly. 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

cd /etc/ansible
- ansible-playbook install-elk.yml elk
- ansible-playbook install-filebeat.yml webservers
- ansible-playbook install-metricbeat.yml webservers
