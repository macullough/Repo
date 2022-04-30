## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly ACCESSIBLE, in addition to restricting INCOMING NETWORK ACCESS to the network.
- _TODO: What aspect of security do load balancers protect? 
ACCESSIBILITY AND TRAFFIC CONTROL

What is the advantage of a jump box?_
ONE PLACE TO MANAGE ALL CONTAINERS ETC AND REMOTE ADMINISTRATION VIA SSH

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the NETOWRK and system FILES.
- _TODO: What does Filebeat watch for?_ MONITORS SYSTEM FOR FILE ALTERATIONS
- _TODO: What does Metricbeat record?_ MONITORS METRICS EX RESOURCES, UP TIME, ETC 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| ELK      | MONITOR  | 10.1.0.5   | LINUX VIA ANSIBLE|
| WEB1     | SERVER   | 10.0.0.5   | LINUX VIA ANSIBLE|
| WEB2     | SERVER   | 10.0.0.6   | LINUX VIA ANSIBLE|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the LOADBALANCER machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:20.40.185.88 
76.123.196.134
 _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by JUMPBOX.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?

JUMPBOX AND WEB1 AND WEB2 HAVE TRUST PEERING ENABLED BETWEEN VN ELK FOR REDUNDANCY AND COMS

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
| WEB1     | NO                  | 10.0.0.4             |
| WEB2     | NO                  | 10.0.0.4             | 
| ELK      | NO                  | 10.0.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

FAST EFFICIENT SCRIPTED IMPLEMENTATION OF DOCKER CONTAINERS THAT ARE EASILY MANAGEABLE AND DEPLOYABLE FROM A SINLE MACHINE

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
Install docker.io

- name: Configure Elk VM with Docker
 
  tasks:
  
    - name: Install docker.io
   
    - name: Install pip3
     
    - name: Install Docker python module
 
    - name: Use more memory

    - name: download and launch a docker elk container

    - name: Enable service docker on boot
 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring

10.0.0.5
10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

FILEBEAT
METRICBEAT

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

FILEBEAT: DETECTS CHANGE TO FILES ON SYSTEM AND COLLECTS LOGS
METRICBEAT: DETECTS RESOURCE METRICS AND ACCESS IMFORMATION

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ANSIBLE.CFG file to /ETC/ANSIBLE.
- Update the HOSTS file to include NEW IP ADDRESS FOR WEBSERVERS AND ELK
- Run the playbook, and navigate to THAT IP to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ .YML > ANSIBLE/FILES

- _Which file do you update to make Ansible run the playbook on a specific machine? 
ANSIBLE.CFG

How do I specify which machine to install the ELK server on versus which to install Filebeat on? ADD AN ENTRY WITH IP IN HOSTS AND SPECIFY AT BEGINNING OF YAML
[webservers]
10.0.0.5 ansible_python_interpreter=/usr/bin/python3
10.0.0.6 ansible_python_interpreter=/usr/bin/python3

[elk]
10.1.0.5 ansible_python_interpreter=/usr/bin/python3

---
- name: Installing and Launch Filebeat
  hosts: webservers

- _Which URL do you navigate to in order to check that the ELK server is running?
http://20.37.2.244:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

 ansible-playbook example.yml