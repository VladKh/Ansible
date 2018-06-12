# Ansible

This Ansible project does:
- create workspace folders
- install Docker
- build Docker image based on Ubuntu 16.04 with HAproxy and Nginx
- deploy services HAproxy as load balancer and Nginx as application
- run Docker 2 containers with the help of docker-compose
- execute health checks to validate correct work HAproxy load balancer between containers


# How to use
To execute on local host:

ansible-playbook -i inventory/local -l local all_in_one.yml -v

To run just health checks if everything is up:

ansible-playbook -i inventory/local -l local health_check.yml -v



URLs to health checks from brouser:

http://localhost:4999/status.html - response from Nginx MASTER container (html page)
http://localhost:4999/status      - Nginx status response from MASTER container
http://localhost:4999/stats       - HAproxy MASTER status (default user:admin, password:1234546)

http://localhost:4998/status.html - response from Nginx SLAVE container (html page)
http://localhost:4998/status      - Nginx status response from SLAVE container
http://localhost:4998/stats       - HAproxy SLAVE status (default user:admin, password:1234546)

http://localhost:9111/            - MASTER Supervisord status
http://localhost:9110/            - SLAVE Supervisord status
