## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](Project%201%20Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

- filebeat.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Available, in addition to restricting Access to the network.
- Load Balancers add layers of security to a website without making significant changes to a website. It highly helps in preventing denial attacks on your system servers. The advantage of a Jumpbox is that It keeps all your internal virtual network machines/containers safe from outside sources.  This allows for you to lock down one point of contact to secure your entire system.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system health.
- Filebeat monitors the log files and/or locations that the user specifies for forwarding and logging data.
- Metricbeat logs the metrics and shows a statistic analysis of the data running across the servers. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux 18_04      |
| DVWA-Web1|    VM    | 10.1.0.5   | Linux 18_04      |
| DVWA-Web2|    VM    | 10.1.0.6   | Linux 18_04      |
| RedElk-VM|    VM    | 10.2.0.4   | Linux 18_04      |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 20.115.30.56

Machines within the network can only be accessed by SSH port 22.
- Jumpbox 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     NO              |  98.122.96.113       |
|  Web-1   |     NO              |  10.1.0.4            |
|  Web-2   |     No              |  10.1.0.4            |
|  Elk     |     NO              |  10.2.0.4            |   

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible is ran from the command line and can make sure all the user scripts/playbooks can be ran uniquely everywhere.

The playbook implements the following tasks:
- Makes changes on the ELK VM
- Install docker.io
- Install python-pip
- Install docker python module
- Download and launch a docker elk stack 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.










### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.5
- 10.1.0.6

We have installed the following Beats on these machines:
- filebeat-7.6.1-darwin-x86_64.tar.gz

These Beats allow us to collect the following information from each machine:
- Filebeat collects the user’s system data (logs) and send it to Kibana where the user can more accurately assess the flow of traffic. The user can expect all traffic and the geographic location it is coming from.  This helps identify potential attacks. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat_config file to the Elk virtual Machine.
- Update the host file to include Servers 10.1.0.5, 10.1.0.6
- Run the playbook and navigate to Kibana to check that the installation worked as expected.

_ Answer the following questions to fill in the blanks: 

- Which file is the playbook? Where do you copy it?_

filebeat.yml, install-elk.yml, metricbeat.yml

- You update the “hosts” file to include the virtual machines that ansible is to be ran on. Secondly, You list below the “webservers” a new category specifically for “ELK” and list that machine in that category. 

- Which URL do you navigate to in order to check that the ELK server is running? http://[your.VM.IP]:5601/app/kibana




















_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.

Run playbook:ansible-playbook filebeat.yml

Edit Playbook: Nano (name of yml file)

