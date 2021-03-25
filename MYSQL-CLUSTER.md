# Creating MYSQL-CLUSTER using docker

### Pre-requisite
 - docker
   * For windows: https://docs.docker.com/docker-for-windows/install/
   * For mac: https://docs.docker.com/docker-for-mac/install/
  
Using mac local machine:

1. Run a docker pull command
```
docker pull mysql/mysql-cluster
```
<img width="565" alt="image" src="https://user-images.githubusercontent.com/56558508/112519049-f2bd2f80-8dd4-11eb-9311-846c961659c0.png">

![image](https://user-images.githubusercontent.com/56558508/112519279-2ac47280-8dd5-11eb-8637-21b88282d3ae.png)


2. Here, we just use a default configuration. Create an internal Docker network that the containers will use to communicate 
```
docker network create cluster --subnet=192.168.0.0/16
``` 
![image](https://user-images.githubusercontent.com/56558508/112519343-3dd74280-8dd5-11eb-9b15-0290137be21c.png)


3. Start the management node

<img width="1105" alt="image" src="https://user-images.githubusercontent.com/56558508/112519531-6cedb400-8dd5-11eb-86f6-cb1972ac75cd.png">


```
docker run -d --net=cluster --name=management1 --ip=192.168.0.2 mysql/mysql-cluster ndb_mgmd
```
<img width="998" alt="image" src="https://user-images.githubusercontent.com/56558508/112519861-be963e80-8dd5-11eb-9110-3728620c5270.png">


4. Then the two nodes
```
docker run -d --net=cluster --name=ndb1 --ip=192.168.0.3 mysql/mysql-cluster ndbd
```

```
docker run -d --net=cluster --name=ndb2 --ip=192.168.0.4 mysql/mysql-cluster ndbd
```

<img width="928" alt="image" src="https://user-images.githubusercontent.com/56558508/112520088-04530700-8dd6-11eb-99ac-969700a8cdb3.png">


5. And the MySQL server node
```
docker run -d --net=cluster --name=mysql1 --ip=192.168.0.10 -e MYSQL_RANDOM_ROOT_PASSWORD=true mysql/mysql-cluster mysqld
```
<img width="1198" alt="image" src="https://user-images.githubusercontent.com/56558508/112520277-306e8800-8dd6-11eb-867d-000bb98b5988.png">


```docker run -d --net=cluster --name=ndb1 --ip=192.168.0.3 mysql/mysql-cluster ndbd
```

6. 
