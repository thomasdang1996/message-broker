**MESSAGE BROKER**  
Ports:
- 8081 - Schema registry (avro schema management)
- 2181 - Zookeeper (leadership management)
- 9092 - Kafka broker (topic management)
- 9021 - Control Center (TBA)

Run: `docker-compose -f docker-compose.yml up`  
Stop: `docker-compose down`