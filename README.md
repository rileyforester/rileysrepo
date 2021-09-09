# rileysrepo
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

~/rileysrepo/diagrams/ELK-Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  ~/rileysrepo/Ansible/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available in addition to restricting in-bound access to the network.

What aspect of security do load balancers protect? 
A load balancer distributes traffic from clients across multiple servers.  It enhances user experience by providing additional security, performance, and scaling. 

What is the advantage of a jump box?
The jump box provides one path to web servers via SSH, and no other protocols are allowed outbound to the Internet or the network.  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jump box and system network.
- Filebeat monitors the log files or locations being specified, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| WebServer-1| Webserver|10.0.0.7  | Linux            |
| WebServer-2| Webserver|10.0.0.8  | Linux            |
| ELK-Stack-VM| Monitoring | 10.1.0.4| Linux          |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-- 73.43.36.121

Machines within the network can only be accessed by jump box provisioner.
Which machine did you allow to access your ELK VM? What was its IP address?
- Jump box provisioner 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 73.43.36.121         |
| WebServer-1|  No               |  10.0.0.4 (jump box) |
| WebServer-2|   No              |  10.0.0.4            |
| ELK        | No                | 10.0.0.4

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

-Agentless –There are no agents or software deployed on the clients/servers to work with Ansible. The connection can be done through the SSH or using the Python.
-English Like Language – To use the Ansible, configure, and deploy the infrastructure is very simple and it is English like the language used called YAML.
-Modular – The Ansible uses modules to automate, configure, deploy, and orchestrate the IT Infrastructure. There are around 750 + modules built-in Ansible.
-Efficient – There are no servers, daemons, or databases required for Ansible to work.
-Features – Ansible comes with a whole lot of features and can be used to manage the Operating systems, IT Infrastructure, the networks, the servers, and services in very less time.
-Secure and consistent – Since the Ansible uses SSH and Python it is very secure and the operations are flawless.
-Reliable – The Ansible Playbook can be used to write programs or the modules and can be used to manage the IT without any downside.
-Performance- The Ansible’s performance is excellent and has very little latency.
-Low Overhead – As it is agentless and does not require any servers, daemons, or databases it can provide a lot of space in the systems and has low overhead in terms of deployment.
-Simple – It is very simple to use and is supported by YAML.

The playbook implements the following tasks:
-Install docker.io
-Install pip3
-Install Docker python module
-Increase virtual memory
-Download and launch a docker
-The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

~/rileysrepo/Images/docker_screenshot.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
WebServer-1 10.0.0.7
WebServer-2 10.0.0.8

We have installed the following Beats on these machines:
-metricbeats

These Beats allow us to collect the following information from each machine:
-Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
-Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

~/rileysrepo/Images/ansible_screenshot

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible control node.
- Update the hosts file to include web servers and ELK VM.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.


- Which file is the playbook? Where do you copy it? 
    -it is the .yml files in /etc/ansible/roles
-  Which file do you update to make Ansible run the playbook on a specific machine? 
    hosts 
    
-  How do I specify which machine to install the ELK server on versus which to install Filebeat on?

~/rileysrepo/Images/hosts_screenshot1.png
~/rileysrepo/Images/hosts_screenshot2.png
    
- _Which URL do you navigate to in order to check that the ELK server is running?
http://20.98.86.197:5601/app/kibana
