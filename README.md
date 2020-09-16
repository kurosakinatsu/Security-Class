# Security-Class
Files accumulated in class.
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!https://github.com/kurosakinatsu/Security-Class/blob/master/Diagrams/ELK_Diagram.png
Diagrams/ELK_Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment
pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.


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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system level usage.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function      | IP Address | Operating System |
|----------|---------------|------------|------------------|
| Jump Box | Gateway       | 10.0.0.4   | Linux            |
| Web-1    | Web Server    | 10.0.0.7   | Linux            |
| Web-2    | Web Server    | 10.0.0.6   | Linux            |
| Web-3    | Web Server    | 10.0.0.9   | Linux            |
| ELKHouse | ELK Container | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
72.220.204.40

Machines within the network can only be accessed by the Jump Box (10.0.0.4).

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses   |
|----------|---------------------|------------------------|
| Jump Box | Yes                 | 72.220.204.40          |
| Web-1    | No                  | 10.0.0.4 10.1.0.4      |
| Web-2    | No                  | 10.0.0.4 10.1.0.4      |
| Web-3    | No                  | 10.0.0.4 10.1.0.4      |
| ELKHouse | Yes                 | 10.0.0.4 72.220.204.40 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because updates can be applied
accross the network instantly through one machine as well as on future machines if necessary.

The playbook implements the following tasks:
- ...Increases the max map count to allow ELK to run
- ...Installs Docker
- ...Installs Python 3
- ...Installs Docker Python Module
- ...Installs Elk in the Docker container
- ...Makes sure Docker is started on machine restarts

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!/c/Users/ps_co/Pictures/Screenshots/docker1.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.7
10.0.0.6
10.0.0.9

We have installed the following Beats on these machines:
Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

Metricbeat collects metrics from your systems and services. From CPU to memory, Redis to NGINX, and much more, Metricbeat is a lightweight way to send system and service statistics to kibana for easy visual comparison.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file from -------------
- Edit /etc/ansible/hosts and add the new machines IP address to the file under the ELK section
- Run the playbook, and navigate to (http://'your new ELK IP':5601/app/kibana) to check that the installation worked as expected.

How do I specify which machine to install the ELK server on versus which to install Filebeat on?
All of the "beats" will be installed on the machines you want to monitor.
ELK will be installed on the machine the monitors the other machines.
