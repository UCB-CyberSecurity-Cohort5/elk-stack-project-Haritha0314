## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

 https://github.com/UCB-CyberSecurity-Cohort5/elk-stack-project-Haritha0314/tree/main/Diagrams

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the **elk-playbook.yml** file may be used to install only certain pieces of it, such as Filebeat.

 https://github.com/UCB-CyberSecurity-Cohort5/elk-stack-project-Haritha0314/blob/main/Ansible/image%20(23).png

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly **available**, in addition to restricting **access** to the network.
- What aspect of security do load balancers protect? - **The load balancers protect the availability aspect of the security. Load balancer distributes the network traffic among the servers.If a server is down, the load balancer diverts the traffic to the working server to ensure the availability and continuity of the connection** 
- What is the advantage of a jump box?_ **Jumpbox protects the servers from public Internet, which in addition reduces the attack surafce.** 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the **system/server** and **system performance**.
- What does Filebeat watch for?_ **Filebeat collects and monitors the logs and forwards it to the tools such as Elastisearch for further analysis** 
- What does Metricbeat record?_ **Metricbeat collects the statistics and metrics such as performance and forwards it to tools such as Elastisearch for further analysis**

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | PublicIp-13.64.64.231, PrivateIP 10.0.0.4  | Linux            |
| RedTeamWeb-1     | Server         |   PrivateIp 10.0.0.5         |    Linux              |
| RedTeamWeb-2  |      Server    |   PrivateIp 10.0.0.6         |  Linux                |
| RedTeamWeb-3  |    Server      |   PrivateIp 10.0.0.7         |   Linux               |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the **Jumpbox** machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-**23.114.192.99**

Machines within the network can only be accessed by.
-Which machine did you allow to access your ELK VM? - **I have set up security group rule such that only my computer can access the ELK server** 
- What was its IP address?_ **23.114.192.99**

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes            | 23.114.192.99   |
|  Virtualnetwork        |  No                   |     10.0.0.4                 |
|      DVWA    |      Yes               |          23.114.92.99            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_
- **It is quicker and easy to manage the configurations from a single docker file. **

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- **Install the Apt packages 
- **Install the pip packages
- **Download the Docker container**
-** Configure the containers**
-** Starts the container**
-** Enables the docker on the reboot** 
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
 - https://github.com/UCB-CyberSecurity-Cohort5/elk-stack-project-Haritha0314/blob/main/Ansible/Docker_ps.jpg

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring_
- **10.0.0.5, 10.0.0.6 and 10.0.0.7**

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed_
- **Metricbeat and Filebeat **

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
- **Metrcibeat collects the metrics and statistics such as system performance, CPU usage etc and Filebeat collects the system logs. **
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the **Playbook** file to **/etc/ansible**.
- Update the **hosts** file to ****include the IP addresses of the hosts and ansible.conig file to include the remote user name.**
- Run the playbook, and navigate to **container** to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- _Which file is the playbook? - **The Playbook is the file with the yml extension and it has the details of the tasks to be accomplished like launching a container.** 
- Where do you copy it?_ **In the /etc/ansible folder**
- _Which file do you update to make Ansible run the playbook on a specific machine? - **the "hosts file.**  
-  How do I specify which machine to install the ELK server on versus which to install Filebeat on?_**this can be specified in the ELK-configuration files and the Filebeat- configurations file. The respective playbooks have the configuration files listed as the source**
- _Which URL do you navigate to in order to check that the ELK server is running? -** https:/[Public IP of the ELK Server:[Port]/app/kibana**

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
-** Download the playbook using a curl command 
- update the hosts file running nano hosts 
- update the ansible.cfg file running nano ansible.cfg
- updating the playbook using nano <nameof the playbook.yml> 
  Running the playbook running ansible-playbook <name of the playbook>.yml **
  
