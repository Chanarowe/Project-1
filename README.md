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

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.http://www.tablesgenerator.com/markdown_tables

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    |DVWA Containers          |            |                  |
| TODO     |          |            |                  |
| TODO     |          |            |                  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
My host machine IP address: 13.77.173.240

Machines within the network can only be accessed by accessing the DVWA container through Jump-Box VM.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? The only machine that can access ELK-1 server is Jump-Box VM through DVWA container throuugh a peering connection with origin IP 10.0.0.8.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 13.77.173.240 10.0.0.8|
| Web-1    | No                  |     10.0.0.8         |
| Web-2    | No                  |     10.0.0.8         |
| Web-3    | No                  |     10.0.0.8         |
| Elk-1    | No                  |     10.0.0.8
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
The main advantage of being able to automate the configuration of machines with Ansible is that it reduces the amount of error when configuring multile machines at one time. Additionally, it simplifies the deployment of software and firewall systems for client machines.


The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

*Install docker
*Download image
*Configure ansible container
*Create ansible playbook
*Run ansible playbook to launch container


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![ELK docker ps](https://github.com/Chanarowe/Project-1/blob/main/elk.jpg)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
* Web-1 VM 10.0.0.9
* Web-2 VM 10.0.0.10
* Web-3 VM 10.0.0.11

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

Filebeat monitors the log files of choosen systems. It then forwards this data to Logstash, or Elasticsearch. This data is able to be viewed via Kibana. Kibana is able to display information in the below screenshot.

Metribeat is is a lightweight shipper that sends data on the status of system services. When metricbeat does not receive these metrics it will send an error event from the host system.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
curl 
https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/filebeat-config.yml
SSH into the control node and follow the steps below:

Copy the filebeat-playbook.yml file to /etc/ansible/roles.
Update the filebeat-config.yml file to include ELK-1 private IP 10.2.0.4 under hosts in Elasticsearch output, and Kibana host.
Run ansible-playbook filebeat-playbook.yml, and navigate to Kibana (http://137.116.68.87:5601/app/kibana) via Elk-1 public IP 137.116.68.87 to check that the installation worked as expected.
TODO: Answer the following questions to fill in the blanks:

Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? In order to specify which machine to run a playbook on you would have to edit /etc/ansible/hosts with the proper group, and internal IP addresses of the selected machines.
_Which URL do you navigate to in order to check that the ELK server is running?
http://137.116.68.87:5601/app/kibana#/home will be the URL to navigate to in order to ensure that the ELK server is running.
