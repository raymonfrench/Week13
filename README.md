# Week13

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/raymonfrench/Week13/blob/main/Network%20Diagram%20Week%2013.PNG "RedTeam Net")

~/Documents/GitHub/Week13/'
Week 13 Network Diagram.drawio'

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - elk.yml

This document contains the following details:
- Installs Docker.io
- Installs Python3-pip
- Installs Docker Module
- Increase memory
- Downloads and Launches dosker elk container
- Publishes ports to run on

  - ansibleconfig.yml
This document contains the following details
- This allows remote user = azadmin

  - hosts
This document contains the following details
- This creats and elk group and allows the webserver and elk group to communicate via python between their IP addresses

  - filebeatsconfig.yml
This document contains the following details
- Adding the ELK server IP addresses and ports

  - Launchfilebeat.yml
This document contains the following details
- Downloads filebeat
- Installs filebeat
- Moves filebeat tot he correct location
- Enables filebeat
- Setsup filebeat

  - metricbeatConfig.yml
This document contains the following details
- Adds IP addresses and ports for Kibana and Elastisearch

  - MetricBeatPlaybook.yml
This document contains the following details
- Downloads Metric Beat
- Installs Metric Beat
- Moves to new directory
- Enables and configures
- Starts Metric Beat

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly STABLE_____, in addition to restricting TRAFFIC_____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Load balancers distribute network traffic accross multiple servers. This ensures no single server bears to much demand. It improves responsiveness. They can also improve security by helping to defend against DDoS attacks
A Jump Box is a secured device that can span two dissimilar security zones. It can be used to manage and access other devices in sepparate zones. 


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _LOG____ and system _FILES____.
- _TODO: What does Filebeat watch for?_ Filebeats monitors logs, collects events and forwards themn to Elastisearch
- _TODO: What does Metricbeat record?_ Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server and send them to Elastisearch

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function       | IP ADDRESS | Operating System |
|------------|----------------|------------|------------------|
| ELK-Server | Log Management | 10.1.0.4   | Linux            |
| Jump Box   | Gateway        | 10.0.0.4   | Linux            |
| VM 1       | Web Server     | 10.0.0.8   | Linux            |
| VM 2       | Web Server     | 10.0.0.9   | Linux            |
| VM 3       | Web Server     | 10.0.0.10  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JUMP BOX_____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_71.ZZZ.XXX0.92 (My Private IP address)

Machines within the network can only be accessed by SSH_____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_JUMP BOX 71.218.230.92

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_Because we will need to do this over and over again and it is easier to keep a file that we can edit and use run commands to install whatever we need. Retyping the commands would be tedious and time consuming. Clicks are $$$.


The playbook implements the following tasks:
- Update Host File
- Create Config File
- Create ansible playbook
- Run ansible-playbook elk.yml
- Varify by going to a browser and accessing Kibana at http;//[your.VM.IP]:5601/app/kibana

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![alt text](https://github.com/raymonfrench/Week13/blob/main/docker_ps_output.PNG "RedTeam Net")

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
10.0.0.8
10.0.0.9
10.0.0.10

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
FILEBEATS 
METRICBEATS

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeats collects logs and system file activity and sends changes to Kibana. If someone were to access you /etc/passwd file it would crate a log of this so you could examine it. Metric beat collects metrics from the operating system and ships them to your output.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the __.yml___ file to /etc/ansible.
- Update the hosts file to include...
[webservers]
    10.0.0.5
    10.0.0.6
    10.0.0.7
   [elkservers]
    10.1.0.4
- Run the playbook, and navigate to ____ to check that the installation worked as expected.
cd /etc/ansible
ansible-playbook elk-playbook.yml
ansible-playbook filebeat-playbook.yml
ansible-playbook metricbeat-playbook.yml

curl http://10.0.0.8:5601 (This command should print HTML to the console.)

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
