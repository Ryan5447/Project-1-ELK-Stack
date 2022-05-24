# Cybersecurity
Project 1 Elk stack

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - Elkinstall.yml

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

What aspect of security do load balancers protect? The load balancer protects against DDoS (Denial of Service) attacks, SSL, offload, authenticate user ID, protects applications from threats, traffic compresstion, and traffic crashing.

What is the advantage of a jump box? Acts as an audit for traffic and a single point where we can manage user accounts. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and sytem logs. 

What does Filebeat watch for? File beat monitors for log files, collects log events and forwards that information to Elasticsearch or longstash for indexing.
What does Metricbeat record? Metricbeatrecords metrics and statistic, and sends the output to programs such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function    | Ip Address | Operating System |
|-----------|-------------|------------|------------------|
| Jump Box  | Gateway     | 10.0.0.4   | Linux            |
| Web 1     | Web Service | 10.0.0.5   | Linux            |
| Web 2     | Web Service | 10.0.0.6   | Linux            |
| Web 3     | Web Service | 10.0.0.8   | Linux            |
| Elk-Stack | Monitoring  | 10.1.0.4   | Linux            |

The Virtual Machines on the internal network are not exposed to the public internet. 

Only the Jump box machince can accept connections from the internet. Access to this machine is only allowed from the following IP addresses:


Machines within the network can only be accessed by jump box provisioner. 
Which machine did you allow to access your ELK VM? jump box provisioner 
What was its IP address? 10.1.0.4
A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed Ip Address      |
|---------------|---------------------|-------------------------|
| Jump Box      | yes/no              | 20.248.207.145/10.0.0.4 |
| Web 1         | no                  | 10.0.0.5                |
| Web 2         | no                  | 10.0.0.6                |
| Web 3         | no                  | 10.0.0.8                |
| Load balancer | yes                 | 20.213.75.213           |
| Elk Stack     | yes/no              | 20.222.13.204           |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
System installation and updates can be done efficiently. Ansible is also easy to set up and use, easy to read, no special coding skills are needed, and is open source.
The playbook implements the following tasks:
Install-Elk
name: set maximum map count in sysctl/systemd
name: docker.io
name: install pip3
name: install Docker module
name: download and launch elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- This ELK server is configured to monitor the following machines:
Web-1 10.0.0.5
Web-2 10.0.0.6
Web-3 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat and Metricbeat
These Beats allow us to collect the following information from each machine:
- Filebeat: Monitors  log files and collects log events and then forwards them to Elasticsearch, or Logstash, or any other specified destination. The filebeat would look at the log events and send them to the ELK-Stack VM.

  Metricbeat: Takes the metrics and statistics acollectred and sends them out to programs such as Elasticsearch or Logstash, or any other specified destination. The metricbeat would look at the uptime of the system or the system logs.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/ansible.
- Update the  /etc.ansible/hosts file to include the ip address of the webservers and the elk-stack.
- Run the playbook, and navigate to http://[personal vm IP]:5601/app/kibanato check that the installation worked as expected.


_ Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it? Update the /etc.ansible/hosts file to include the ip address of the webservers and the elk-stac
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
etc/ansible/hosts include the ip address of the webservers and elk server.
- Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
Open Gitbash and ssh in your jump box ssh azadmin@20.248.207.145
Sudo docker ps
Sudo docker start vigilant_kirch (vigilant_kirch is my container)
Sudo docker attach vigilant_kirch
Cd /etc/ansible to work under the ansible file
Ssh-keygen to your webserver get the ssh_rsa.pub key in order to connect 
Create a playbook file use nano playbook to make file and playbook
Nano ansible.cfg add remote_user=azadmin to which server you want to see
Run ansible-playbook myplaybook.yml (the playbook you created with nano) and run the file
