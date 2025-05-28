# posts
.NET Microservices: CQRS &amp; Event Sourcing with Kafka

* CQRS: separate read write
-data is more often read than altrerd or created
-scale C&Q APIs independently (few lock contentions when performing C&Q in the same model)
-optimised read and write schemas


* Event sourcing - DP
-defines and approach to storing all the changes made to an object/entity as a sequence of immutable events to an ES.
-contains a complete auditable log
-the state of the object(aggregate) can be recreated at any timeframe just by replaying the event store
-improves the write operation, since events are simply appended to the ES


* KAFKA
OS, streaming platform

# SETUP DOCKER 

* Create Docker Network 
command: docker network create --attachable -d bridge mypostsdockernetwork
output: fc213e8cc830a29db417dae6ad2c705ee010025207a1ce8d506ba7f10bdc12dc

* Check version of docker compose
command: docker-compose --version
output: Docker Compose version v2.31.0-desktop.2

* Create a folder 'docker' at root level and create a docker-compose.yml file 
  command: docker-compose up -d
  command: docker ps (see the running containers)

* observed the kafka docker container is restarting frequently --see logs 
  kafka 05:36:33.47 INFO  ==> 

kafka 05:36:33.47 INFO  ==> ** Starting Kafka setup **

kafka 05:36:36.38 ERROR ==> Kafka requires at least one process role to be set. Set the environment variable KAFKA_CFG_PROCESS_ROLES to configure the process roles for Kafka.

/opt/bitnami/scripts/libkafka.sh: line 357: KAFKA_CFG_PROCESS_ROLES: unbound variable

kafka 05:36:36.38 ERROR ==> KRaft mode requires an unique node.id, please set the environment variable KAFKA_CFG_NODE_ID

/opt/bitnami/scripts/libkafka.sh: line 408: KAFKA_CFG_LISTENER_SECURITY_PROTOCOL_MAP: unbound variable

kafka 05:36:36.39 WARN  ==> Kafka has been configured with a PLAINTEXT listener, this setting is not recommended for production environments.

kafka 05:36:37.94 INFO  ==> 

kafka 05:36:37.94 INFO  ==> Welcome to the Bitnami kafka container

kafka 05:36:37.94 INFO  ==> Subscribe to project updates by watching https://github.com/bitnami/containers⁠

kafka 05:36:37.94 INFO  ==> Did you know there are enterprise versions of the Bitnami catalog? For enhanced secure software supply chain features, unlimited pulls from Docker, LTS support, or application customization, see Bitnami Premium or Tanzu Application Catalog. See https://www.arrow.com/globalecs/na/vendors/bitnami/⁠ for more information.

* So we deleted the containers and created again with updated yml 
  command: docker-compose down -v

* Run mongo db
  command: docker run -it -d --name mongo-container -p 27017:27017 --network mydockernetwork --restart always -v mongodb_data_container:/data/db mongo:latest
  
output: 
Digest: sha256:9f67b6bafda002f7bcad9939e4d84c3b4e9b11ffff6c1f9fab3f77e30c646304
Status: Downloaded newer image for mongo:latest
fc57aa81f828ca950ed41e1a162b14b68522f0838dda9d81e137f4eed6a40f4f





