# JBoss Build and configure with Ansible and Vagrant  

Requirements:  
- Requires Ansible 1.2 or newer  
- Expects CentOS/RHEL 6 or 7 hosts  

Steps:  
Run the vagrant command to build the VM and kickoff the ansible playbook:  

```vagrant up```  
  
The HelloWorld application will be available at ```http://127.0.0.1:8080/helloworld```  

The Ticket Monster application will be available at ```http://127.0.0.1:8080/ticket-monster```  

To run the build and deploy individually to a VM you can modify the host file and run the individual playbooks below.  
 
## Standalone JBoss Deployment  
  
These playbooks deploy a very basic implementation of JBoss Application Server, version 7. To use them, first edit the "hosts" inventory file to contain the hostnames of the machines on which you want JBoss deployed, and edit the group_vars/all file to set any JBoss configuration parameters you need. Then run the playbook, like this:  
  
```ansible-playbook -i inventory/hosts build-jboss.yml```  
  
When the playbook run completes, you should be able to see the JBoss Application Server running on the ports you chose, on the target machines.  
  
## Application deployment  
  
The playbook deploy-application.yml may be used to deploy the HelloWorld and Ticket Monster demo applications to JBoss hosts that have been deployed using build-jboss.yml, as above. Run the playbook using:   
  
```ansible-playbook -i inventory/hosts deploy-application.yml```



