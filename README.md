# Virtualbox - Vagrant - Ansible - Windows Primer  
Steps to run the Provision and Configuration  
1. Install Virtualbox - Verify install by running the VirtualBox Manager UI  
2. Install Vagrant - Verify the install by vagrant --version at the command line.  This is only a CLI (Command line interface).  
3. Install Git, if not already done  
4. Clone the repo, git clone https://github.com/kpeeples/codecamp.git  
5. In the directory run, vagrant up to build the VM; Note: You can switch to a certain vagrant box in the vagrant file depending on which stack you want from my ansible playbooks. The trusty64 (Ubuntu) for the LAMP stack and the centos for the jboss stack which is configured with Ansible playbooks I provided.  the lamp playbook is using apt-get for ubuntu and the jboss playbook is using the yum for centos.  This installs necessary packages.Depending on whether you created the ubuntu or centos that determines which ansible file to use.  
6. Run vagrant ssh to connect to the terminal for the VM.  If everything completed properly you will see the VM in the virtualbox manager.  Note if you receive a vt-x BIOS error then you must enable the BIOS setting.  see below [1]  
7. This means you have a running machine.  Now you must configure it manually or run a config script.  Puppet/Ansible/chef allow you to do this manually.  We are using Ansible which uses playbooks.  
8. To setup Ansible on a Windows 10 machine I recommend following this link - https://www.jeffgeerling.com/blog/2017/using-ansible-through-windows-10s-subsystem-linux  Go through the Installing Bash on Windows 10 and Installing Ansible sections.  The inventory/hosts (192.168.33.34) files for ansible will contain the IP of the VM you created above.  
9. Open a bash shell from windows.  run, git clone https://github.com/kpeeples/codecamp.git  
10. FOR the LAMP stack with the trusty64 enabled and run with vagrant up, run the command ansible-playbook playbook.yml -i inventory --become from the provision lamp directory in the bash shell.  Then you can browse to http://192.168.33.34 to see the Apache page.  
OR depending on which of the boxes you used in the vagrantfile  
10. FOR the JBOSS stack with the centos enabled in the vagrantfile, run the command  ansible-playbook playbook.yml -i inventory --become from the provision jboss directory in the bash shell.  he HelloWorld application will be available at http://127.0.0.1:8080/helloworld and The Ticket Monster application will be available at http://127.0.0.1:8080/ticket-monster  
NOTE: You can add the provision call for ansible playbooks in the vagrantfile but the host OS needs to be linux as we have ansible running in the bash subsystem.  
  
[1] To run Oracle VM Virtual Box / VMware machines on 64-bit host there is a need to enable Virtualization Technology (VTx) and Virtualization Technology Directed I/O (VTd).  Usually these setting are disabled on the level of BIOS.  To enable VTx and VTd you have to change corresponding settings in the BIOS.  Here is an example how to do it for HP Compaq or similar PC:  
1. Start the machine.  
2. Press F10 to enter BIOS.  
3. Security-> System Security  
4. Enable Virtualization Technology (VTx) and Virtualization Technology Directed I/O (VTd).  
5. Save and restart the machine.  
