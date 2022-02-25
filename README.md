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
- File beat watches for log activity and harvests new log data from specified locations.
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function                             | IP Address | Operating System   |
|----------|------------------------------------- |------------|--------------------|
| Jump Box | Gateway                              | 10.0.0.7   | Linux Ubuntu 18.04 |
| Web-3    |WebServer - Docker Container for DVWA | 10.0.0.13  | Linux Ubuntu 18.04 |
| Web-4    |WebServer - Docker Container for DVWA | 10.0.0.14  | Linux Ubuntu 18.04 |
| ELKServer|Server for ELK Stack                  | 10.1.0.4   | Linux Ubuntu 18.04 |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box-provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 198.101.32.242 & *private unlisted

Machines within the network can only be accessed by ssh from the 10.0.0.7 
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses              |
|----------------------|---------------------|---------------------------------  |
| Jump Box Provisioner | Yes                 | 198.101.32.242 & *privateUL       |
| Web-3 & Web-4        | No (only through LB)| 10.0.0.7 public via 104.45.238.195|
| ELKServer            | No                  | 10.0.0.7                          |
| Load Balancer        | Yes                 |                                   |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
