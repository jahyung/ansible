
yum install epel-release
yum install ansible


adduser ansible-user
passwd ansible-user
ssh-keygen
ssh-copy-id ansile-user@192.168.0.7


vi hosts.ini
ansible-target-host ansible_host=192.168.0.7 ansible_user=ansible-user

ansible -m ping -i hosts.ini all

vi /etc/hosts

[webserver]
192.168.0.7
#[a-c]server.example.org

vi mysql.yml
---
- name: install mysql
  hosts: webserver
  become: true
  become_user: root
  gather_facts: true
  tasks:
    - name: "install mysql"
      package: name=mysql-server state=present
   
 - name: adduser
   hosts: webserver
   become: true
   become_user: root
   gather_facts: true
   tasks:
     -name: "add user mysql"
      action: adduser mysql_user
      
vi os.yml
---
-  name: os update
   hosts: webserver
   become: true
   task: 
   -name : update to latest os
   action: yum name=centos state=latest
   notify: restart centos
   
   
   
