## Elk Commands and Steps

This guide should help with step-by-step commands to SSH, start and attach containers, and ultimately navigate to the Kibana Dashboard for the ELK server.

- PowerShell

  - `ssh redadmin@40.87.27.108`

  - `sudo docker container list -a`

  - `sudo docker start tender_swartz`

  - `sudo docker attach tender_swartz`

  - `cd /etc/ansible `

  - `ls`

    - ELK-playbook.yml	ansible.cfg	filebeat-config.yml	hosts	metricbeat-config.yml	metricbeat-playbook.yml	pentest.yml

  - `ssh sysadmin@10.1.0.4`

  - `sudo docker container start elk`

  - http://13.83.51.111:5601/app/kibana#/home (https://github.com/cltempleton1127/ELK-Stack-Project/blob/main/Linux/Metricsbeat_kibana_success.png)

# Troubleshooting:
  - Re-run playbooks
  - Double check IP listed in URL
  - Make sure it is http not https
