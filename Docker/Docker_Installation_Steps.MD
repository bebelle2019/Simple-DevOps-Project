# Installing Docker on Amazon Linux server

### Pre-requisites
1. Lunch new Amazon Linux EC2 Instance
1. Change hostname to docker-host

## Installation Steps

1. Add this script to data user
```sh
#!/bin/bash
sudo -i
#Change hostname to docker-host
hostnamectl set-hostname docker-host
#Patch
yum install docker -y
systemctl enable --now docker
#Create dockeradmin user
useradd dockeradmin
#Add password to user
echo 1qaz2wsx | passwd dockeradmin --stdin
#Add a dockeradmin to docker group to manage docker
usermod -aG docker dockeradmin
```

### Validation test
1. Create a tomcat docker container by pulling a docker image from the public docker registry
   ```sh
   docker pull tomcat:9
   docker run --name test-tomcat-server -p 8080:8080 tomcat:9
   docker run -d --name test-tomcat-server -p 8080:8080 tomcat:9
   d = dettach
   ```
# It may not work because the webapps is on a different location
### Fix HTTP Status 404: NOT FOUND
  ``` sh
    LOGIN TO THE CONTAINER
    docker exec -it <container_name> /bin/bash
    Check to make sure you have ROOT directory under webapps is not copy from webapps.dist
    cp -R webapps.dist/* webapps
    Then refresh the websitet to verify
    
    To avoid this issue, we can use tomcat:8.0 image version for our build
    ```
    




