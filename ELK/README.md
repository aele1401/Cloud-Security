## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram](https://github.com/aele1401/Cloud-Security/blob/main/ELK/Diagrams/ELK_Diagram.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above or portions of the deployment. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, a Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to limiting access to the network.

Integrating an ELK server allows administrators to easily monitor the vulnerable VMs for changes to the log files and system metrics.

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.1   | Linux            |
| Web1     |VM w/Docker| 10.1.0.11  | Linux            |
| Web2     |VM w/Docker| 10.1.0.9   | Linux            |
| Web3     |VM w/Docker| 10.1.0.12  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public internet. 

Only the Jump Box machine can accept connections from the internet. Access to this machine is only allowed from specific IP addresses that are whitelisted.


Machines within the network can only be accessed by web servers.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Local machine IP     |
| Web VMs  | No                  | None                 |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it automates drudgerous tasks.

The playbook implements the following tasks:
- Installs docker, python module, images, and enables docker service
- Increases system memory
- Downloads and launches docker containers (i.e., web, elk, etc.)
- Installs, sets up, starts, and enables filebeat & metricbeat

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker Diagram](https://github.com/aele1401/Cloud-Security/blob/main/ELK/Diagrams/dockerps.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.11
- 10.1.0.09
- 10.1.0.12

I have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow the administrator to collect the following information from each machine:
- Filebeat to collect file logs that helps with detecting malicious activity..
- Metricbeat collects metric information, which shows system health, performance, etc. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration (preconfigured) file to your ansible playbook.
- Update the ansible.cfg file to include your ELK server IP address.
- Run the playbook, and navigate to your kibana site to check that the installation worked as expected.
