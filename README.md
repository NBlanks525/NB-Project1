## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[ELK Installation YAML File](https://github.com/NBlanks525/NB-Project1/blob/main/Ansible/Install_ELK.yml)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.

  - etc/ansible/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

![Network Diagram](https://github.com/NBlanks525/NB-Project1/blob/main/Diagrams/NoelleBlanksProject1NetworkTop.jpg)

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availabilty, in addition to restricting traffic to the network.
- Load balancers protect the availability. The advantage of jump box is to manage devices in a separate security zone on the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat watches for any information in the file system that has been changed. 
  Metricbeat takes the metrics and statistics that collects and ships them to the output you specify. 

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web 1    | Webserver| 10.0.0.5   | Linux            |
| Web 2    | Webserver| 10.0.0.6   | Linux            |
| ElkVM    | VM       | 10.1.0.4   | Linux           


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 23.96.96.86 

Machines within the network can only be accessed by Jump Box VM 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 23.96.96.86          |
| Web 1    | No                  |  10.0.0.4           |
| Web 2    | No                  |  10.0.0.4          
| ElkVM    | No                  |  10.0.0.4  

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The main advantage is that you can put commands into multiple servers from a single playbook.

The playbook implements the following tasks:
- install docker.io 
- install python-pip
- install docker 
- sysctl -w m.max_map_count=262144
- launch docker container 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker ps screenshot](https://github.com/NBlanks525/NB-Project1/blob/main/Diagrams/DockerPSimage.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1 10.0.0.5
- Web 2 10.0.0.6

We have installed the following Beats on these machines:
- filebeat and metricbeat 

These Beats allow us to collect the following information from each machine:
- Filebeat collects the changes done. Metric beat collects metrics and statistics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yml file to ansible folder.
- Update the config file to include...
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

- Which file is the playbook? Where do you copy it?_ 
   /etc/ansible/files/filebeat-config.yml
- Which file do you update to make Ansible run the playbook on a specific machine?
   /etc/ansible/host file 
 How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
  
- Which URL do you navigate to in order to check that the ELK server is running?
168.62.216.232:5601/app/kibana 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ansible-playbook 
