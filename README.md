## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1yv-YazHlRn10bd0enjX9ZRhnTfX71P4e/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the __elk.yml___ file may be used to install only certain pieces of it, such as Filebeat.

  - SEE ELK.YML in Ansible Folder

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliabe and available in the event a server goes down, in addition to restricting ___traffic__ to the network.
-  What aspect of security do load balancers protect? What is the advantage of a jump box?

A load balancer defends an organization against distributed denial-of-service (DDoS) attacks. It does this by directing attack traffic from the corporate server to a public cloud provider. The load balancer can also request a username and password before granting access to your website to protect against unauthorized access.

The advantage of a jump box is it allows you to minimize attack surface therefoer making an attack harder. This is because you can move towards whitelisting IP Addresses. This is having and requiring authentication to have any communication with the servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __logs___ and system __traffic___.

-  What does Filebeat watch for?  Filebeat watches all the logs and monitors the log files and locations that are specified
-  What does Metricbeat record?  Metricbeat collects all the statistics and metrics from Filebeat and sends them to places such as Logstash

The configuration details of each machine may be found below.


|         Name         | Function | IP Address |   OS  |
|:--------------------:|:--------:|:----------:|:-----:|
| Jump-Box-Provisioner | Gateway  | 10.0.0.4   | Linux |
| Web-1                | Gateway  | 10.0.0.5   | Linux |
| Web-2                | Gateway  | 10.0.0.6   | Linux |
| Web-3                | Gateway  | 10.0.0.7   | Linux |
| Elk-Server           | Gateway  | 10.1.0.4   | Linux |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- Add whitelisted IP addresses-  73.37.164.222

Machines within the network can only be accessed by Jump-Box-Provisioner.

- Which machine did you allow to access your ELK VM? What was its IP address?

Jump-Box-Provisioner    10.0.0.4/52.165.165.230
 

A summary of the access policies in place can be found in the table below.

|  Virtual Machine Name | Publicly Accessible | Allowed IP Addresses         |   |
|:---------------------:|---------------------|------------------------------|---|
| Jump-Box-Provisioner  |         Yes         | 73.37.164.222                |   |
| Web-1                 |          No         | 52.165.165.230               |   |
| Web-2                 |          No         | 52.165.165.230               |   |
| Web-3                 |          No         | 52.165.165.230               |   |
| Elk-Server            |         Yes         | 73.37.164.222 |52.165.165.230|   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-  What is the main advantage of automating configuration with Ansible?

The biggest advantage is the simplicty of use.  It is a relatively easy configuration to set up and use, and is a pretty powerful program as it lets you model highly complex IT workflows

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.

-Install Docker.io

-Install pip3, which is a python module

-updates the system to use more memory

-downloads and launches docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

This was run successfully.  No screenshot available.

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring- 

-- Web-1  10.0.0.5
-- Web-2  10.0.0.6
-- Web-3  10.0.0.7

We have installed the following Beats on these machines:

- Filebeat and Metricbeat
 
These Beats allow us to collect the following information from each machine:
-In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc

The filebeat and metricbeat allows us to see things such as if a user was previewing a file or when a user logged on or off.  These metrics measure everything that is clicked on or typed in.  It is a great way to keep logs of all user activity.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.  NOT SURE HOW TO ANSWER THIS?  IT IS POORLY WORDED.

- Update the __"hosts" in the ansible.config___ file to include..."webservers" and "elkservers"

- Run the playbook, and navigate to _ https://10.1.0.4:5601/app/kibana___ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?  

When creating your playbook, you update your "hosts:" to whomever the host is for the machines.  In this case it was either "webservers" or "elkservers"

- _Which URL do you navigate to in order to check that the ELK server is running?

https://10.1.0.4:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.

ansible-playbook elk.yml

You can put any playbook in where "elk.yml" is, but to run the playbook you need the command "ansible-playbook <whateverplaybookyoucreated.yml>"

The files will be updated when the playbook is run.
