## MESSAGE BROKER
### How to run Message Broker
1) clone project: `git clone https://github.com/thomasdang1996/message-broker.git`
2) Install and run [Docker Desktop](https://www.docker.com/products/docker-desktop/)
3) Go to project file, run command `docker-compose -f up`. To stop, use `docker-compose down`
4) Ports of each component:
    - http://localhost:8081 - Schema registry (avro schema management)
    - http://localhost:2181 - Zookeeper (leadership management)
    - http://localhost:9092 - Kafka broker (topic management)

### Schema Registry
To receive and send messages, add a new schema to the registry via REST. For this project, add `CreateAccountPayload`:
```
POST 
url: http://localhost:8081/subjects/CreateAccountPayload/versions   
Request body:
   {
      "schema": "{\"type\":\"record\",\"name\":\"CreateAccountPayload\",\"namespace\":\"avrogenerated.accountmanager\",\"fields\":[{\"name\":\"username\",\"type\":{\"type\":\"string\",\"avro.java.string\":\"String\"}},{\"name\":\"email\",\"type\":{\"type\":\"string\",\"avro.java.string\":\"String\"}}]}",
      "schemaType": "AVRO"
   }
```
For more info about Schema Registry API, see [documentation](https://docs.confluent.io/platform/current/schema-registry/develop/api.html#schemas).

### Other projects
After adding new schema to the registry, clone and run following projects:
- [PearStore BE](https://github.com/thomasdang1996/pear-store-be.git) - Main project
- [AccountManager BE](https://github.com/thomasdang1996/account-manager-be.git) - for receiving message payload from PearStore BE
