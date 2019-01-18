# Apigee OPDK Port Check

The purpose of thie Ansible role is report whether Apigee ports are in face accessible.


Requirements
------------

T
  
Role Variables
--------------

Two collections are expected. 

host_list: A list of hosts from which to check the taret ports.

ports: A list of ports that should be found accessible. 

timeout_port: The amount of time that we should wait for a response. Default =  10

private_address: The private IP asssigned. 


Dependencies
------------

he following Ansible roles are used by this role: 

* apigee-opdk-settings-private-address
* apigee-opdk-settings-region
* apigee-opdk-settings-management-server
* apigee-opdk-settings-cassandra
* apigee-opdk-settings-ldap
* apigee-opdk-settings-postgres
* apigee-opdk-port-check 
  
Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

     - name: Validate that Openldap port requirements are met
       hosts: ldap
       tags: ['ldap']
       strategy: free
       vars:
         ports:
         - "{{ ldap_ports }}"
       roles:
         - { role: apigee-opdk-port-check, host_list: "{{ groups['ms'] }}" }    
         
         
         
         

License
-------

Apache 2.0

Author Information
------------------

Carlos Frias
