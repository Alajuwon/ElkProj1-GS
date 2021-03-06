# ElkProj1-GS
Elk Stack project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/Alajuwon/ElkProj1-GS/blob/main/Images:diagram_filename.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the configuration file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: install-elk.yml_

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
Load Balancers protect the server and reroutes traffic to another server to monitor traffic from potential DDOS attacks. A jump-box keeps the VMs IP addresses from public exposure. 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Network and system logs.
- _TODO: What does Filebeat watch for?_ Data for the file system
- _TODO: What does Metricbeat record?_  Machine metrics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| DVWA-Web1| Azure    | 10.0.0.5   | Linux            |
| DVWA-Web2| Azure    | 10.0.0.6   | Linux            |
| Elk-Server|         | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box Pro machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by A home IP Addess.
- _TODO: Which machine did you allow to access your ELK VM? WEB 1 What was its IP address?_10.0.0.5

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No YES          | 10.0.0.5 10.0.0.6    |
| Web1     |        NO           |   10.0.0.5           |
| Web2     |        NO           |   10.0.0.6           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ Setting up ansible configuration using SSH! 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ... Install Docker 
- ... Install Python
- ... Increase the memory
- ... Download the sebp/elk image 
- ... Publish the three (3) ports - 5044, 5601, 9200

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/docker_ps_output.png


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
Web-1: 10.0.0.5
Web-2: 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
- Metricbeat
- Filebeat

These Beats allow us to collect the following information from each machine:
Filebeats collects log files from Apache web servers and Metricbeats is used to monitor file system, memory, network stats and the VM stats. Filebeat logs information about the file system, including which files have changed and when.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/filebeat/files.
- Update the filebeat-configuration.yml file to include... The IP address with the IP address of your ELK machine
- Run the playbook, and navigate to ELK server's IP from your web browser to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ 
The filebeat-playbook.YML file is the playbook file to be copied to /etc/filebeat/roles
- _Which file do you update to make Ansible run the playbook on a specific machine? You update the filebeat-config.yml file. How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ Which ever IP address of the web1 or web2 you want to use
- _Which URL do you navigate to in order to check that the ELK server is running?
 http://your-Elk-IP:5601/app/kibana
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

- Use the CURL command to download the config file
- Update the config file with the IP address of the Elk machine. Delete the default one Ex: [Your-Elk-IP:5601]
- Save and create a filebeat-playbook.yml
- Download and install the .deb file using the dpkg command
- Configure these commands inside the file: filebeat modules enable system - filebeat setup - service filebeat start - Enable the filebeat service on boot
- Then go back to the Filebeat installation page on the ELK server
- scroll to Step 5: Module Status and click Check Data
- You should see the date / The ELK server receiving logs from each of your Web VMs!
