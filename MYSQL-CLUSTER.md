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
docker run -p 3360:3360 -d --net=cluster --name=mysql1 --ip=192.168.0.10 -e MYSQL_RANDOM_ROOT_PASSWORD=true mysql/mysql-cluster mysqld
```

<img width="1291" alt="image" src="https://user-images.githubusercontent.com/56558508/112537003-1f7b4200-8de9-11eb-975e-dff98354d5c5.png">


6. The server will be initialized with a randomized password that will need to be changed, fetch it from the log
```
docker logs mysql1 2>&1 | grep PASSWORD
```

<img width="630" alt="image" src="https://user-images.githubusercontent.com/56558508/112537895-31a9b000-8dea-11eb-8053-7f1f3f68afd4.png">


7. Login, input the password that you got from step 6. If there is an error: «ERROR 2002 (HY000): Can't connect to local MySQL server through socket» then the server has not finished initializing yet.
```
docker exec -it mysql1 mysql -uroot -p -h 127.0.0.1
```

<img width="710" alt="image" src="https://user-images.githubusercontent.com/56558508/112538974-6833fa80-8deb-11eb-8c9e-af4eeb4c8969.png">


8. Change the password
```
ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass';
```

<img width="473" alt="image" src="https://user-images.githubusercontent.com/56558508/112539046-78e47080-8deb-11eb-9f02-b490673832e9.png">


* just to see the status information from the server

<img width="847" alt="image" src="https://user-images.githubusercontent.com/56558508/112539128-90235e00-8deb-11eb-8fc3-a2521e9b9e59.png">


9. To check the database type **show databases;**

<img width="176" alt="image" src="https://user-images.githubusercontent.com/56558508/112539310-cfea4580-8deb-11eb-9de3-9dfe578726c5.png">


10. From here to validate if you can create a database, type **create database nameOfDatabase;**

<img width="255" alt="image" src="https://user-images.githubusercontent.com/56558508/112539555-19d32b80-8dec-11eb-8139-b84ead729e8d.png">


11. Check if it is added by **show databases;**

<img width="177" alt="image" src="https://user-images.githubusercontent.com/56558508/112539701-471fd980-8dec-11eb-87de-c5730737b6a9.png">


12. Open a new terminal and start the container with an interactive management client to verify that the cluster is up

```
docker run -it --net=cluster mysql/mysql-cluster ndb_mgm
```

<img width="744" alt="image" src="https://user-images.githubusercontent.com/56558508/112522462-a07e0d80-8dd8-11eb-8a6b-98838133ffe8.png">


13. Run **show** command to see the cluster status

<img width="463" alt="image" src="https://user-images.githubusercontent.com/56558508/112540234-e47b0d80-8dec-11eb-8186-36d14457f9e3.png">



