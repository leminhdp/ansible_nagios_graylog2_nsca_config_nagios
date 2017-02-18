
Role Name
=========

**ansible_nagios_graylog2_nsca**  
Graylog2 script and nagios automatic configuration to have nsca scripts for your streams. (Send notifications to nagio

Starting this work based on: 
https://bashinglinux.wordpress.com/2013/05/26/graylog2-and-nagios-integration-2/

I have seen this also: 
https://github.com/frederikhappel/graylog2-plugin-alarmcallback-nsca
But as this 4y old and I don't support java I will not use it. 


Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

Check [defaults/main.yml](defaults/main.yml) file for details


Configure graylog for exec
--------------------------

Checkout doc: https://github.com/nksft/graylog2-plugin-exec#usage

Create a **"Execute Command Alarm Callback"** on the **"Manage alerts"** page of your stream. Enter the requested configuration and save. Make sure you also configured alert conditions for the stream so that the alerts are actually triggered.

Add Bash command: `/usr/local/sbin/graylog2-alert.sh`  (or whatever you have put on ansible_nagios_graylog_nsca_script)

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Not a dependency but you can use https://github.com/CoffeeITWorks/ansible_nagios_graylog2_nsca to complete the graylog2 nsca config script for your streams.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
- name: Config nagios hosts service and host for graylog nsca stream services
  hosts: nagios4_servers
  become: yes
  environment: "{{ proxy_env }}"
  roles:

    - role: ansible_nagios_graylog2_nsca_config_nagios
      tags:
        - role::ansible_nagios_graylog2_nsca
        - role::ansible_nagios_graylog2_nsca_config_nagios
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
