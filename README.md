# kafka-examples 

Examples of how to use Kafka

## Setting up Kafka

1. Please make sure that Docker is already installed in the system,
If not, install from https://www.docker.com/products/docker-desktop

2. If on Windows O/S, open a Powershell window.
If on Mac OS or Linux, open a Terminal window.

3. Navigate to the directory where the exercise files are downloaded.
This directory would contain the kafka-single-node.yml file

4. Execute the following command from this directory

        docker-compose -f kafka-single-node.yml up -d

5. Check if the containers are up and running

        docker ps


6. To shutdown and remove the setup, execute this command in the same directory

        docker-compose -f kafka-single-node.yml down


## Using Kafka

To use Kafka we need the following commands:

### Logging into the Kafka Container

        docker exec -it kafka-broker /bin/bash

### Navigate to the Kafka Scripts directory

        cd /opt/bitnami/kafka/bin

### Creating new Topics

        ./kafka-topics.sh \
            --zookeeper zookeeper:2181 \
            --create \
            --topic kafka.learning.tweets \
            --partitions 1 \
            --replication-factor 1

        ./kafka-topics.sh \
            --zookeeper zookeeper:2181 \
            --create \
            --topic kafka.learning.alerts \
            --partitions 1 \
            --replication-factor 1

### Listing Topics

        ./kafka-topics.sh \
            --zookeeper zookeeper:2181 \
            --list

### Getting details about a Topic

        ./kafka-topics.sh \
            --zookeeper zookeeper:2181 \
            --describe


### Publishing Messages to Topics

        ./kafka-console-producer.sh \
            --bootstrap-server localhost:29092 \
            --topic kafka.learning.tweets

### Consuming Messages from Topics

        ./kafka-console-consumer.sh \
            --bootstrap-server localhost:29092 \
            --topic kafka.learning.tweets \
            --from-beginning

### Deleting Topics

        ./kafka-topics.sh \
            --zookeeper zookeeper:2181 \
            --delete \
            --topic kafka.learning.alerts