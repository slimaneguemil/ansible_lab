ansible --version
# list all targets oin inventory
ansible-inventory --list

#display current config 
ansible-config view
# list variables of config
ansible-config list

# ping  machine named 'debian'
ansible -m ping debian
ansible -m ping all
ansible -m ping test --limit ubuntu

# play a book  'ping.yml'
ansible-playbook ping.yml

#check parameters of config
ansible-config dump --only-changed

#add user at target host
ansible debian -m user -a "name=newbie uid=4000 state=present"

#list all module
ansible-doc -l | grep ping
ansible-doc ping

ansible debian -m service -a "name=sshd state=started"
ansible debian -m shell -a "service --status-all"
ansible debian -m user -a "name=test password=test state=present"
 ansible debian -m shell -a "tail /etc/passwd"
ansible debian -m user -a "name=test password=test state=absent"
 or userdel test

# demo install nginx et check url
   57  ansible debian -m package -a "name=nginx state=present"
   58  ansible debian -m shell -a "service --status-all"
   59  ansible debian -m shell -a "service --status-all | grep nginx"
   61* ansible debian -m service -a "name= state=started"
   62  ansible debian -m shell -a "service --status-all | grep nginx"80"
   64  ansible debian -m package -a "name=curl state=present"
   65  ansible debian -m shell -a "curl http://localhost:80"
   66  ansible-doc uri
   70  ansible-doc uri | grep =
   69  ansible debian -m uri -a** "url=http://localhost:80"

