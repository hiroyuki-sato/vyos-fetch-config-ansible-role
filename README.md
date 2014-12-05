## Ansible role for VyOS.

This is an ansible role to collect configuration from VyOS hosts.

## Installation step

Clone this repo to your Ansible roles directory

    mkdir roles
    cd roles
    git clone https://github.com/hiroyuki-sato/vyos-fetch-config-ansible-role.git vyos


Here's an example how to use this role. create vyos_config.yml

    - hosts: all
      user: vyos
      roles: 
        - vyos

Create inventory file. ex. inventory.ini

    # VyOS IP or FQDN
    10.10.10.10

## Directory example

    ./configs/10.10.10.10.config   # output of show config
    ./configs/10.10.10.10.gen-sets # output of show configuration commands
    ./inventory.ini
    ./vyos/README.md
    ./vyos/tasks/main.yml
    ./vyos_config.yml

## Execution example


    PLAY [all] ********************************************************************
    
    GATHERING FACTS ***************************************************************
    ok: [10.10.10.10]
    
    TASK: [vyos | generate current config set] ************************************
    changed: [10.10.10.10]
    
    TASK: [vyos | generate current config.] ***************************************
    changed: [10.10.10.10]
    
    TASK: [vyos | copy file gen-sets] *********************************************
    ok: [10.10.10.10]
    
    TASK: [vyos | copy file] ******************************************************
    ok: [10.10.10.10]
    
    TASK: [vyos | delete conf files] **********************************************
    changed: [10.10.10.10]
    
    PLAY RECAP ********************************************************************
    10.10.10.10             : ok=6    changed=3    unreachable=0    failed=0   


You will find configuraiton file in configs directory. 


