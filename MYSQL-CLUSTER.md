# Creating MYSQL-CLUSTER using docker

### Pre-requisite
 - docker
  #### For windows: https://docs.docker.com/docker-for-windows/install/
  #### For mac: https://docs.docker.com/docker-for-mac/install/
  
Followed the steps from https://hub.docker.com/r/mysql/mysql-cluster/ using mac local machine.

1. Run a docker pull command
```
docker pull mysql/mysql-cluster
```
<img width="565" alt="image" src="https://user-images.githubusercontent.com/56558508/112519049-f2bd2f80-8dd4-11eb-9311-846c961659c0.png">


2. Here, we just use a default configuration. Create an internal Docker network that the containers will use to communicate 
```
docker network create cluster --subnet=192.168.0.0/16
``` 
3. Start the management node
```
docker run -d --net=cluster --name=management1 --ip=192.168.0.2 mysql/mysql-cluster ndb_mgmd
```


 



