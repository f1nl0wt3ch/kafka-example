# KAFKA FUNDAMENTALS

## Terms

- **Broker**
- **Consumer**
- **Producer**
- **ETL** stands for extract, transform and load.
- **Connector**
- **Source**
- **Sink**
- **CDC** Change data capture
- **Zookeeper**

## Set up a CDC pipeline using Debezium Source Connector

- **docker run -it --rm --name my-zookeeper -p 2181:2181 -p 2888:2888 -p 3888:3888 zookeeper:3.5.5** create a zookeeper.
- **docker run -it --rm --name my-kafka -p 9092:9092 --link my-zookeeper:my-zookeeper debezium/kafka:1.0**
- **docker run -it --rm --name my-mysql -p 3306:3306 -v ./mysql.cnf:/etc/mysql/conf.d/mysql.cnf -e MYSQL_ROOT_PASSWORD=password -e MYSQL_USER=kafka -e MYSQL_PASSWORD=password -e MYSQL_DATABASE=kafka mysql:5.7**
- **docker run -it --rm --name mysqlterm --link mysql mysql:5.7 sh -c 'exec mysql -h "$MYSQL_PORT_3306_TCP_ADDR" -P "$MYSQL_PORT_3306_TCP_PORT" -uroot -p "$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'**
- **GRANT SELECT, RELOAD, SHOW DATABASES, REPLICATION SLAVE, REPLICATION CLIENT ON *.* TO 'my-mysql' IDENTIFIED BY 'password''**