# ELK-Project
Example of the creation of a virtual network in Microsoft Azure
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Azure Virtual Network (1)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network. Load balancing plays an important security role in modern cloud computing. It protects the organization from Distributed Denial of Services (DDoS) Attacks, shifting attack traffick to public load providers, instead of undermining corporate servers.

A Jump Box provides organizations with a reliable and consistent method for launching and administrating tasks. It is a hardener server that administrators use to access other servers via ssh. One of the most important roles a jump box play is to provide security to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

Filebeat watches for log data and system traffic. It is considering a piece of software that forwards and centralizes log data. Metricbeat collects metrics and statistics from the operting system and from services runing on the server. it takes all the collected data and send them to the specified ouput. such as Elasticsearch or Logstach.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function | IP Address    | Operating System |
|-----------|----------|---------------|------------------|
| Jump Box  | Gateway  | 10.0.0.4      | Linux            |
| DVWA-Web1 | VM       | 10.0.0.5      | Linux            |
| DvWA-Web2 | VM       | 10.0.0.6      | Linux            |
| ELK-server| VM       | 10.1.0.5      | Linux            | 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
200.194.13.43

Machines within the network can only be accessed by SSH.

The machine that is able to connect to the Elk Server (10.1.0.5) is the Jump-Box (10.0.0.4)


A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| Jump Box   | Yes                 | 10.0.0.5 10.0.0.5    |
| WEB-1      | No                  | 10.0.0.4             |
| WEB-2      | No                  | 10.0.0.4             |
| ELK-SERVER | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The primary benefit of using Ansible is that it allows IT administrators to automate tasks and focus on more important taks.

The playbook implements the following tasks:
- The steps of the ELK installation play were the following ones:
- ...Configure ELK VM with Docker
- ... Install Docker.io
- ... Install pip3


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



Path with the name of a screenshot of docker ps output](Images/docker_ps_output.png)
https://drive.google.com/file/d/1nfrS7F4cC2LxTFwI-xONYB3U6R_mf2tP/view?usp=sharing

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines I am monitoring_
- 10.0.0.5
- 10.0.0.6
- 20.0.0.4


We have installed the following Beats on these machines:

- filebeat-config.yml
- filebeat-playbook.yml

These Beats allow us to collect the following information from each machine:

Filebeat is a light weight shiper for forwarding and centralizing data. It monitors log files and locations and forwards them to ElasticSearch. It can handle garbage collection (GC) logs, for example.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-platbook.yml file to the /etc/ansible/roles/ directory.
- Update the Filebeat configuration file to include the Private IP of the ELK server to the ElasticSearch and Kibana sections of the configuration file.

- Run the playbook, and navigate to http://13.87.185.203:5601/app/kibana#/home to check that the installation worked as expected.


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

- ssh RedAdmin@Jumpbox public IP
- sudo docker container list -a
- sudo docker start container
- sudo docker attach container
- cd /etc/ansible/
- cd /etc/ansible/roles
- ansible-playbook filebeat-playbook.yml
- Elk-server public IP@5601/app/kibana

