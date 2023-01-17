# Ansible-CodeBeamer

This will setup a codebeamer server complete with my-sql

## Platform requirements
The machines required are given below. If you can allocate more compute resources, its better :-

    1. Codebeamer Server - 4 vcpu / 16 gib ram

## Setup SSH 
Create ssh keys required for ansible to use certificates for connections over ssh
```
    ssh-keygen     (accept default options)

    cd .ssh

    ls -l          (view to ensure keys are generated)

    ssh-copy-id  *<user>@<hostname>*     (repeat for all nodes)
```
## Update inverntory file

Update the variables etc as required in the inventory file and role files

## Running the Playbook

Update the playbook hosts file as required
```yaml
  ansible_user: user
  ansible_connection: ssh
```

## Create Certificate key strings from generated certificate
```
   openssl pkcs12 -in "C:\Temp\codebeamer.pfx" -nocerts -nodes -out "c:\Temp\codebeamer.key"
   openssl rsa -in "c:\Temp\codebeamer.key" -out "c:\Temp\codebeamer.private.key"
   openssl rsa -in "c:\Temp\codebeamer.key" -pubout -out "c:\Temp\codebeamer.public.key"       
```

Command Line to run :-
```
    ansible-playbook -i inventory.yaml playbook.yaml -K 
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-K reperesents --ask-become-pass: 
ask for privilege escalation password



<br></br>
## ToDo
```
    1. ... Move Data directory https://www.thegeekstuff.com/2016/05/move-mysql-directory/
```

