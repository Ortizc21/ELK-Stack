# ELK-Stack
Elk stack deployment
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
![image](https://user-images.githubusercontent.com/84930015/137049287-0bafb9e0-1540-4470-9eae-2b682e1d576c.png)



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - Filebeats.yml

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
- The load balancerhelps keep the network available as well as help protect the network from denial-of-service attacks

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metric.
- Logs files that are monitored by filebeat.
- Any metrics monitored by metricbeat.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| web 1    | VM       | 10.0.0.8   | Linux            |
| web 2    | VM       | 10.0.0.9   | Linux            |
| elkweb   | ELKStack | 10.01.8    | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- my home IP

Machines within the network can only be accessed by using SSH through the jumpbox.
- 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | My home IP           |
| web1 & 2 | no                  | Home IP, 10.0.0.4    |
| ELKweb   | no                  | Home IP, 10.0.0.4    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible makes the scripts run between the systems. 

The playbook implements the following tasks:
- Installs docker onto the ELKStack
- Downloads and launches docker containers.
- Enables docker service.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- web1 10.0.0.8
- web2 10.0.0.9

We have installed the following Beats on these machines:
- filebeat
- metricbeat

These Beats allow us to collect the following information from each machine:
- filebeat collect log events which we can track and monitor.
- metricbeat collects metric data that can be used to track the user systems health.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration file to etc/ansible.
- Update the host file to include private IP addresses of the machines that are going to be installed and configured with the ELKStack.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.
- _Which file is the playbook? Where do you copy it?
The playbook file is the YAML file that is provided, and it should be copied into the /etc/ansible directiory in the ansible container.
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
 The hosts file in the etc/ansible directory needs to be updated and you can specify which machines to install filebeat one by adding the private IP addresses to the hosts file.
- _Which URL do you navigate to in order to check that the ELK server is running?
http://40.122.165.128:5601/app/kibana
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
