## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Red_Team_Diagram](https://user-images.githubusercontent.com/78993470/122680711-8cbb2b00-d1be-11eb-88b7-1ff0f533a9c7.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  -[Link of all ansible playbooks](https://github.com/bernice99/Elk-Stack_Project/tree/main/Ansible)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly avaliable, in addition to restricting unauthorized access to the network. Load balancers can be defined as the process of distributing traffic across multiple servers. Load balacers serve an important security role by adding an extra layer of security to your websites. It plays a role in protecting websites from hackers and also prevnts DDos attacks. This brings us to the advantage of a jumpbox. It serves as an entry point in providing an all in one access point for administrative tasks. This plays a vital role by protecting other VM's and also serving as the only way to access other VM's within the Resource Group.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic. 
Filebeat watches for log files and locations specified then collects log events.
Metricbeat records the metrics and statistics from servers and systems running on the server.

The configuration details of each machine may be found below.

| Name                | Function | IP Address  | Operating System |
|---------------------|----------|------------ |------------------|
| Jump-Box-Provisoner | Gateway  |13.64.179.187| Linux            |
| Web-1               | Server   | 10.0.0.5    | Linux            |
| Web-2               | Server   | 10.0.0.6    | Linux            |
| Elk__Server         | Server   | 10.3.0.4    | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
My Public IP Address: 142.114.239.158

Machines within the network can only be accessed by the Jumpbox-Provsioner. The IP address is 13.64.179.187
_
A summary of the access policies in place can be found in the table below.

| Name                | Publicly Accessible | Allowed IP Address |
|---------------------|---------------------|--------------------|
| Jump-Box-Provisoner | Yes                 | 142.114.239.158    |
| Web-1               | No                  | 13.64.179.187      |
| Web-2               | No                  | 13.64.179.187      |
| Elk__Server         | No                  | 13.64.179.187      |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the main advantage of using Ansible to automate configuration is because of how it makes the installation process easier when it comes to deploying multiple servers. It is also very simple and easy to set up and use.


The playbook implements the following tasks:
- Install docker.io
- Install phython3.pip
- Install docker python module
- Download and launch Docker DWVA web container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker_ps_output](https://user-images.githubusercontent.com/78993470/122680890-8f6a5000-d1bf-11eb-99f8-54f6f44036e5.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
  
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat: watches for logs and collects events related to those files and locations

Metricbeat: records metrics and statistical data from the operating system and services that are running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install_elk_yml file to /etc/ansible directory.
- Update the hosts file to include the IP address of Web 1 and 2, and also the Elk server and must have python3 assigned as the interpreter.
- Run the playbook, and navigate to the Elk server to check that the installation worked as expected.

- Which URL do you navigate to in order to check that the ELK server is running?
- http://(publicIPofElkServer):5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
To run a playbook: ansible-playbook (nameoffile.yml)
To update a file: nano (nameoffile)
