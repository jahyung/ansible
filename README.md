
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
[a-c]server.example.org
