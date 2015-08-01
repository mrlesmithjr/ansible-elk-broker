Role Name
=========

Installs ELK Stack Role (ELK-Broker)

Requirements
------------

Prior to using this role you will want to add your nodes to the appropriate inventory group and create the corresponding group_vars/group with variables defined. You should create 3 elk-broker nodes. Examples below.
#####hosts inventory
````
[elk-nodes]
elk-broker-1
elk-broker-2
elk-broker-3

[elk-broker-nodes]
elk-broker-1
elk-broker-2
elk-broker-3

````

Role Variables
--------------

#####group_vars/elk-nodes
````
---
es_cluster_name: vagrant
es_cluster_setup: true
es_network_publish_host: _eth1:ipv4_
es_min_master_nodes: 2
redis_allow_remote_connections: true
````
#####group_vars/elk-broker-nodes
````
---
es_data_node: false
es_master_node: true
````

Dependencies
------------

````
mrlesmithjr.ntp
mrlesmithjr.rsyslog
mrlesmithjr.snmpd
mrlesmithjr.timezone
mrlesmithjr.redis
mrlesmithjr.elasticsearch
mrlesmithjr.elk-kibana
````

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: elk-broker-nodes
      roles:
         - { role: mrlesmithjr.elk-broker }

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
