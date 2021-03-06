ansible-zabbix_modules
======================

Ansible modules to manage Zabbix servers 
Currently only supports hosts (zabbix_host) and hostgroups (zabbix_group) More might come.

## Related projects
* Ansible Zabbix agent to deploy agents on ubuntu nodes https://github.com/ahelal/ansible-zabbix_agent
* Ansible Zabbix server to deploy zabbix servers on ubuntu node https://github.com/ahelal/ansible-zabbix_servers


## Install
download/clone/fork this project
And you have 4 options

1. Configure your bash variable/profile with the following ```export ANSIBLE_LIBRARY=$ANSIBLE_LIBRARY:/pathto/ansible-zabbix_modules```
2. Configure your ansible.cfg 
3. Put the files in ansible/library/monitoring (not recommended)

## Dependency
These module depends on pyzabbix in order to operate. 
**Update**
pyzabbix is integrated in the module so no need to install seperate.


##Usage
For more detailed help after installation use ```ansible-doc zabbix_host ``` and ```ansible-doc zabbix_group ``` 

Examples 
```
# Create a new hostgroup with name "production"
- zabbix_groups: 
     name=production
     login_url=https://zabbix.example.com/zabbix
     login_user=Admin
     login_password=pass
```
```
# Delete a hostgroup with name "development
- zabbix_groups: 
     name=development
     login_url=https://zabbix.example.com/zabbix
     login_user=Admin
     login_password=pass
     state=absent
```

```
# Create a new host with name "host1"
- zabbix_host: 
     name=host1
     login_url=http://zabbix.example.com/zabbix
     login_user=Admin
     login_password=pass
     groups="production,web"
     visible="TheHost1"
     status=yes
     dns="host1.example.com"
     port="10050"
     templates="Template OS Linux,anotherTemplate"                 
```
```
# Delete a hostgroup with name "host1"
- zabbix_host: 
     name=production
     login_url=http://zabbix.example.com/zabbix
     login_user=Admin
     login_password=pass
     state=absent
```                 
