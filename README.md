# Ansible

There are two ansible files.
- container.yml -> To deploy a Docker Container along with docker setup on a machine.
- django.yml -> To deploy docker-compose (postgres-django-nginx) via ansible script

Ansible hosts file contain multiple servers so that container is deployed across servers.

Make sure python intepreter is correctly configured in host and remote machine and also selinux context.

I have used CentOS 7 as a remote host.

To deploy a Docker Container on remote host:

 - ansible-playbook -u root container.yml
   
To deploy docker-compose remote host
 - ansible-playbook -u root django.yml
 
 Sample output:
 ```
 [root@localhost django_project]# sudo docker ps
CONTAINER ID        IMAGE                  COMMAND                  CREATED             STATUS              PORTS                           NAMES
e29e7b10374b        django_project_nginx   "nginx -g 'daemon of…"   20 seconds ago      Up 19 seconds       80/tcp, 0.0.0.0:8081->443/tcp   nginx
c9de71a3f1d9        django_project_web     "/bin/sh /home/app/w…"   21 seconds ago      Up 19 seconds       8000/tcp                        django
1adacd696c3a        postgres:12.1-alpine   "docker-entrypoint.s…"   22 seconds ago      Up 20 seconds       5432/tcp                        postgres
 ```
