sudo -i
mv ansible.cfg ansible.cfg_backup
ansible-config init --disabled -t all > ansible.cfg   
vim ansible.cfg # change host_key_checking=False
chmod 400 clientkey.pem

ansible wbe01 -m ping -i inventory

Use cases of adhoc command
1. Reboot server

#ADHOC COMMANDS
ansible web01 -m ansible.builtin.yum -a "name=httpd state=present" -i inventory
ansible web01 -m ansible.builtin.yum -a "name=httpd state=present" -i inventory --become
ansible webservers -m ansible.builtin.yum -a "name=httpd state=present" -i inventory --become
ansible webservers -m ansible.builtin.yum -a "name=httpd state=absent" -i inventory --become
ansible webservers -m ansible.builtin.yum -a "name=httpd state=present" -i inventory --become
ansible webservers -m ansible.builtin.service -a "name=httpd state=started enabled=yes" -i inventory --become
vim index.html
ansible webservers -m ansible.builtin.copy -a "src=index.html dest=/var/www/html/index.html" -i inventory --become


123  ansible webservers -m yum -a "name=httpd state=absent" -i inventory --become
  124  ansible-playbook -i inventory web-db.yml
vim web-db.yml
ansible-playbook -i inventory web-db.yml
ansible-playbook -i inventory web-db.yml -v
ansible-playbook -i inventory web-db.yml -vv
ansible-playbook -i inventory web-db.yml -vvv
ansible-playbook -i inventory web-db.yml -vvvv
ansible-playbook -i inventory web-db.yml --syntax-check # syntax check
ansible-playbook -i inventory web-db.yml -C # dry run

sudo vim /etc/hostname # put control has hostname
sudo hostname control # and run this command

## db setup on centos
yum search | grep -i mysql
ansible-galaxy collection install community.mysql

## ansible cli vars
ansible-playbook -e USRNM=cliuser -e COMM=cliuser vars_precedence.yaml

## ansible gather facts
ansible -m setup [web01]

## ntp conf agent
/etc/ntpsec/ntp.conf # ubuntu
/etc/ntp.conf # centos

## Roles in ansible
:%s/^    // to replace 4 spaces from the beggining in vim
