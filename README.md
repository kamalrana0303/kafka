# kafka
documentation for Kafka using docker
#zookeeper
 docker run -it  --name zookeeper -p 2181:2181 -p 2888:2888 -p 3888:3888 zookeeper:3.5.5  
#Kafka
 docker run -it --name kafka -p 9092:9092 --link zookeeper:zookeeper debezium/kafka:1.0
#mysql
 docker run -it --name mysql -p 3306:3306  -v ~/mysql.cnf:/etc/mysql/conf.d/mysql.cnf -e MYSQL_ROOT_PASSWORD=password -e MYSQL_USER=root -e MYSQL_PASSWORD=password -e MYSQL_DATABASE=ecom mysql:5.7

# mysql.cnf
[mysqld]
skip-host-cache
skip-name-resolve

user=mysql
symbolic-links=0

server-id = 223344
log_bin = mysql-bin
expire_logs_days = 1
binlog_format = row


# Run mysql and bash into msyql container
docker run -it --rm --name mysqlterm --link mysql mysql:5.7 sh -c 'exec mysql -h "$MYSQL_PORT_3306_TCP_ADDR" -P "$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'


# Grant access
GRANT SELECT, RELOAD, SHOW DATABASES, REPLICATION SLAVE, REPLICATION CLIENT ON *.*  to  'ecom' IDENTIFIED BY 'password';

# Grant privilleges
GRANT ALL PRIVILEGES ON ecom.* TO 'root'@'%';

e.g GRANT ALL PRIVILEGES ON database.* TO 'username'@'localhost' IDENTIFIED BY 'password';


![image](https://github.com/kamalrana0303/kafka/assets/46786713/62083937-bdc3-4b2c-889f-306ee8f7b399)

![image](https://github.com/kamalrana0303/kafka/assets/46786713/84511301-aef2-4c12-ae66-41b6510bd9f9)

![image](https://github.com/kamalrana0303/kafka/assets/46786713/94fe0619-8a44-4b06-b063-6bff251ca106)

#deploy debezium connector using curl command

![image](https://github.com/kamalrana0303/kafka/assets/46786713/cb5842f9-51ac-48a3-8d3c-dd36b1c772b0)




