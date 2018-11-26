# Zabbix Project - Task

This repository contains files for building docker images of docker applicance with a ubuntu image. For the full repo with all the flavours refer to the below repository.

https://github.com/zabbix/zabbix-docker


## Getting Started
You would need a mac os x machine or any linux machine to setup the project and run the tasks. This would create a docker container of zabbix-appliance which has the zabbix server, front-end and backend mysql server.


### Prerequisites

Following are the required tools/software:
```
Docker
For installing docker refer https://docs.docker.com/install/#pre-releases

```

```
Ansible
For installing ansible refer https://docs.ansible.com/ansible/2.5/user_guide/intro_getting_started.html
```
```
Git

GitBash or git to be available to clone the repository.
```


### Installing

Given below is the step by step instructions for running this project

Step 1:

```
Run the shell script from the following location
go to the folder
zabbix-app/zabbix-appliance/ubuntu
run the script build.sh
Note: no parameters are supplied

This will build the docker image for the zabbix-appliance for ubuntu.

If successful the result would be as below 
"Successfully tagged zabbix-appliance:ubuntu-latest"
```

Step 2:

```
Run the docker image with the following command

docker run --name test-zabbix-appliance -p 80:80 -p 10051:10051 -d zabbix/zabbix-appliance:ubuntu-latest
The will start a zabbix-appliance within a docker container.

Once successfull type the below command to verify if the docker is running
docker ps -a
This will show the container id along with ports for both front-end and database
```


## Running the ansible playbooks

Following are the ansible playbooks which should to run both the tasks as requested.

Task #1

```
Move the root folder ZABBIX-TASK, go to folder ansible-playbooks
run the following command ansible-playbook tasks/createhosts.yml 

This will create new host.

For verification in a browser window open http://localhost/

This will show the zabbix app, provided you are running on port 80, otherwise use appropriate port such as  http://localhost:<PORT>/

Login with default user Admin and password zabbix

Go the tab Configuration -> Hosts, if all goes well you can see the hosts you've just created using ansible

```

Task #2

```
Run the next task by running the command below: 
ansible-playbook tasks/exp-template.yml 

You'll be able to see the output in the tasks folder as output.json, which is the template exported in json format.

```

### Cleanup

Do a cleanup

```
Type the command docker ps -a
Note the container image id.
Type the command docker rm <containerId> to remove the docker container
Delete all the files / folders downloaded by git hub

```



## Authors

* **Shyju Eswaramangalath** - *Linked In* - [LinkedIn](https://www.linkedin.com/in/shyju-subramanian-73083617/)




## Acknowledgments

* Zabbix documentations
* Google
* Ansible Documentaton
