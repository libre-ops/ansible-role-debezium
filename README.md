Debezium role
=============

This is an Ansible role for installing [Debezium](https://debezium.io/), an open-source tool for **Change Data Capture** 
that streams database changes to Kafka Connect.

See the latest Debezium docs [here.](https://debezium.io/docs/) 


Defaults
--------

Check out all the defaults [here.](defaults/main.yml) The default connector is `postgres`, but you can override it, 
along with the version: 
```
debezium_connector_name: debezium-connector-postgres
debezium_version: "0.9.5.Final"
```

Setup
-----

You'll most likely be using Kafka Connect, and either the `protobufs` or `wal2json` plugins. These all require 
additional setup that isn't included here. The defaults for interacting with Kafka assume the use of `Confluent`:
```
kafka_user: cp-kafka
kafka_group: confluent
kafka_plugins_path: /usr/share/java
kafka_connect_service: confluent-kafka-connect
```


Example playbook
----------------

```
- name: Install Debezium
  hosts: webservers

  roles:
    - role: debezium
```
