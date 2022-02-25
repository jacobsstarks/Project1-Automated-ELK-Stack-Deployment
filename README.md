## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](/Images/Homework12_JacobStarks.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the project1-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  The [project1-playbook.yml](/Playbooks/project1-playbook.yml) file will load all four playbooks in succession, allowing for quick install on active virtual machines.

  The playbooks are separated as follows:

  [pentest.yml](/Playbooks/pentest.yml) establishes the DVWA containers on the virtual machines within the NightoftheLivingBread virtual network

  [install-elk.yml](/Playbooks/install-elk.yml) uses the connection from the Jump-Box-Provisioner machine to install the ELK Server on the ELKStack virtual network VM

  [filebeat-playbook.yml](/Playbooks/filebeat-playbook.yml) installs filebeat monitoring program on the virtual machines within the NightoftheLivingBread virtual network

  [filebeat-playbbok.yml](/Playbooks/filebeat-playbook.yml) installs filebeat monitoring program on the virtual machines within the NightoftheLivingBread virtual network

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
Because load balancing is able to direct traffic efficiently among vms, the resulting availability is increased and better serves to fulfill the desired state of the CIA triad.
The Jump-Box-Provisioner allows for more secure access and modification of vms, bolstering the integrity of the network, it also provides a buffer between direct access of the webservers, ensuring administrative control over tasks concerning those machines.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the event logs and system metrics.

- Filebeat watches for log activity and harvests new log data from specified locations
- Metricbeat records the metrics from the OS and services running on the server

The configuration details of each machine may be found below.


| Name     | Function                             | IP Address | Operating System   |
|----------|------------------------------------- |------------|--------------------|
| Jump Box | Gateway                              | 10.0.0.7   | Linux Ubuntu 18.04 |
| Web-3    |WebServer - Docker Container for DVWA | 10.0.0.13  | Linux Ubuntu 18.04 |
| Web-4    |WebServer - Docker Container for DVWA | 10.0.0.14  | Linux Ubuntu 18.04 |
| ELKServer|Server for ELK Stack                  | 10.1.0.4   | Linux Ubuntu 18.04 |

### Access Policies

The machines on the internal network are not exposed to the public Internet. They are protected by network security group inbound rules, and in the case of the vms, aided by the loadbalancer.

Only the jump-box-provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 198.101.32.242 & *private unlisted

Machines within the network can only be accessed by ssh from the 10.0.0.7 private ip on Jump-Box-Provisioner, but the DVWA container on Web-3 & Web-4 is allowed from allow-listed ips
- The ELKServer is accessible via 10.0.0.7 ssh connections using port 5601

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses              |
|----------------------|---------------------|---------------------------------  |
| Jump Box Provisioner | Yes                 | 198.101.32.242 & *privateUL       |
| Web-3 & Web-4        | No (only through LB)| 10.0.0.7 public via 104.45.238.195|
| ELKServer            | No                  | 10.0.0.7                          |
| Load Balancer        | Yes                 |                                   |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because multiple instances of the server can be deployed quickly.

The [install-elk.yml](/Playbooks/install-elk.yml) implements the following tasks:
1. Installs Docker
2. Installs Python3-pip
3. Installs the Docker module
4. Increases virtual memory to 262144 and use via systctl module
5. Downloads and launches the docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Elk Installation Success](/Images/sebp_elk_761.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

| Name     | Function                             | IP Address | Operating System   |
|----------|------------------------------------- |------------|--------------------|
| Web-3    |WebServer - Docker Container for DVWA | 10.0.0.13  | Linux Ubuntu 18.04 |
| Web-4    |WebServer - Docker Container for DVWA | 10.0.0.14  | Linux Ubuntu 18.04 |


We have installed the following Beats on these machines:
-FileBeat
-MetricBeat

These Beats allow us to collect the following information from each machine:
- Filebeat watches for log activity and harvests new log data from specified locations. For example, Filebeat can show us information like when a sudo command or an ssh login occurred
- Metricbeat records the metrics from the OS and services running on the server. This information is very useful for troubleshooting performance and detecting anomalies like high cpu usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat and metricbeat configuration files to each vm in the backend pool.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.


- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
