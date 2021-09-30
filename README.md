# ELK-Stack-Project
University of RIchmond Cybersecurity Bootcamp ELK stack Project

![Project1_ELK-Stack-Diagram (2)](https://user-images.githubusercontent.com/86531330/135138057-96071aa4-23d6-4e23-bf85-5014dcf51638.jpg)


I created an ELK stack that allows the automatation of monitoring the performance of multiple virtual machines in one database. By using the ELK Server in conjunction with containers, the benefits are:

- Scalability and Elasticity
- Efficiency of Resources
- Ideal for Team Distribution and Collaboration Efforts
- Increased Security
- App Isolation

More information about [Cloud Domain, Containers, and the Security Benefits](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Additional%20Resources/Interview%20Question%20about%20Containers.md)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above, or select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build
- Bonus - Commands Used

### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, increase availability, in addition to restricting access to the network.

The Jump Box is a tool used to connect to devices within a security zone. Because it was set up with SSH Keys instead of passwords, it protects the machines from DDoS attacks.

Integrating an ELK server allows users to easily monitor the webservers for changes to the logs and system metrics and statistics.

Filebeat collects data about the file system. Metricbeat collects machine metrics, such as uptime.

The configuration details of each machine may be found below.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web1    | Server   | 10.0.0.5   | Linux            |
| Web2    | Server   | 10.0.0.6   | Linux            |
|Web3      | Server   | 10.0.0.9   | Linux            |
|ELK-server| Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

My home IP address (72.84.246.10)

Machines within the network can only be accessed by "My PC" via the Jumpbox. ![See Diagram](https://user-images.githubusercontent.com/86531330/135138057-96071aa4-23d6-4e23-bf85-5014dcf51638.jpg)

The Jumpbox VM was allowed access to the ELK VM. Jumpbox VM: IP 10.0.0.4   My PC: via SSH IP 72.84.246.10. 
A summary of the access policies in place can be found in the table below.

|   Name   | Publicly Accessible | Allowed IP Addresses  |
|----------|---------------------|-----------------------|
| Jump Box |        Yes           |      72.84.246.10     |
|   Web1  |        No           |10.0.0.4|
|   Web2  |        No           |10.0.0.4|
|   Web3  |        No           |10.0.0.4|
|ELK-Server|        No           |10.0.0.4|


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the playbook, much like the ones for Filebeat and Metricbeat, saved time and remove [some] elements of human error.  

[Link to Playbooks and Config Files](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Ansible)

|ELK_Playbook tasks    |
|----------|
| Install: docker.io |
| Install: Python-pip  |
| Install: docker |
|Launch docker container: elk|

This [screenshot](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Linux/START_ELK-sudo-docker-ps_sysadmin%40ELK-SERVER_%20~.png) displays the result of running `docker ps` after successfully configuring the ELK instance.

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

| Name     | Function | IP Address |
|----------|----------|------------|
| Web1    | Server   | 10.0.0.5   |
| Web2    | Server   | 10.0.0.6   |
| Web3    | Server   | 10.0.0.9   |

We have installed the two Beats on these machines.  These Beats allow us to collect the following information from each machine:

- **Filebeat**: can handle audit logs, deprecation logs, gc logs, server logs, and slow logs. 

- **Metricbeat**: collects machine metrics. For example, Metricbeat can be used to monitor and analyze system CPU, memory and load.

The Kibana dashboard provides lots of system information, including: heatmap, sankey chart, response codes, unique visitors, total requests, etc. 
These data points are helpful for collecting and revieweing output like you see here in this [Kibana Exploration Activity](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Additional%20Resources/Kibana%20Exploration.docx.pdf)

### Using the Playbook

There were four playbooks used when creating this network.  

| Playbook     | Action(s) |
|----------|----------|
| [pentest](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Ansible/pentest.yml) | This is the initial playbook to add a container to the Jump Box and install docker.io, pip3, Docker python | 
| [ELK Playbook](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Ansible/ELK-playbook.yml) | This playbook increased the resources for the ELK server, add the container, and install docker.io, pip3, Docker python  | 
| [filebeat-playbook](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Ansible/filebeat-playbook.yml) | This playbook pulled the download, config file, and .yml for Filebeat | 
| [metricbeat-playbook](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Ansible/metricbeat-playbook.yml) | This playbook pulled the download, config file, and .yml for Metricbeat  | 

  - [Playbooks and Config Files](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Ansible)
  
Since [pentest](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Ansible/pentest.yml) was the playbook created as part of the Cloud Security unit, it would need to be implemented first to have an Ansible control node configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

- Copy the playbook file to /etc/ansible.
- Update the [Ansible Host File](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Ansible/hosts.txtt) to include the webservers and ELK server (and IP addresses).
- Run the playbook, and navigate to command line to check that the installation worked as expected.
- Playbook: [ELK-Playbook](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Ansible/ELK-playbook.yml) Location: /etc/ansible/ELK_playbook.yml


[PowerShell Steps to enable Kibana Dashboard](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Linux/ELK%20Command%20and%20Steps.md)

To check if the ELK-SERVER is running, the URL is: http://13.83.51.111:5601/app/kibana. 

If you shut your machines down, and need to run this after restarting your ELK-SERVER VM, it would just need to be run with "http://DYNAMICIP:5601/app/kibana". The DYNAMIC IP will be your ELK-SERVER public IP address. This will only need to be done if you have a dynamic IP as it changes every time you shut down and restart your machine. 
  
[Kibana Dashboad Success](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Linux/Metricsbeat_kibana_success.png)

## Bonus
[Link to Bonus: Commands](https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Linux/Bonus.md)

## Group
- [Courtney Templeton](https://github.com/cltempleton1127)
- [Josh Black](https://github.com/joshblack07)
- [Laura Pratt](https://github.com/laurapratt87)

