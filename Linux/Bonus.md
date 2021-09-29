## Bonus

The following are the specific commands the user will need. Some commands are written generally since the command would be dependent on specific information (username, IP, container name, etc.)

- `sudo docker ps` will display which containers are present and running.
- `sudo docker start [container name]` will start the specified container in PowerShell; If in GitBash, the command is: 'sudo docker container start tender_swartz'. 
  - PowerShell Example: `sudo docker start tender_swartz`
- `sudo docker attach [container name]` will log the user into the specific container in PowerShell ('sudo docker container atttach [container name]' if in GitBash). 
  - Example: `sudo docker start tender_swartz`
- `ssh username@IP` will log a user into a new machine as long as it is running and allowing access. 
  - Example: `ssh sysadmin@10.1.0.4`
- `ansible-playbook [playbook name].yml` will run the playbook. 
  - Example: `ansible-playbook ELK-playbook.yml`
- `curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat >> /etc/ansible/filebeat-config.yml` will pull the Filebeat config file from the specified website.
- the `nano` command that was used to add/edit configuration files, playbooks, hosts, etc. 
  - Example: `nano ELK-server.yml`
