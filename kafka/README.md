Requirement:

Storing the kafka topics data into mongodb.

Prerequisite:

docker network create --driver=bridge --subnet=192.168.0.0/16 sample-network
Create a zookeeper and mongodb containers. For reference check zookeeper and mongodb in github.

Versions:

MongoDB: 5.0.1
zookeeper:3.6.3
kafka:2.8.0

Once the containers are up and running then do the following.

Copy the file MongoDbSinkConnector.properties to docker volume of kafka/config/ folder and change the values as per requirement.

I have downloaded the kafka-connect-mongodb library from https://www.confluent.io/hub/mongodb/kafka-connect-mongodb and the version is 1.6.1 and copied the file into docker container /opt/bitnami/kafka/libs folder

Restart the docker container.

Testing:

Open three sessions of the terminal.

In First session run the following command.

docker exec -it kafka_container /opt/bitnami/kafka/bin/connect-standalone.sh /opt/bitnami/kafka/config/connect-standalone.properties /opt/bitnami/kafka/config/MongoDbSinkConnector.properties

In second session run the following command.

docker exec -it kafka_container /opt/bitnami/kafka/bin/kafka-console-producer.sh --broker-list kafka.example.com:9092 --topic test_sam
>{"name":"JyothiRavi", "age":24}

In third session connect to MongoDB container and check the database for the collections and data.
