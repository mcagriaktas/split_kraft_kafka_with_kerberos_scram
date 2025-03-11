### CREATE TOPIC AND LIST
```bash
/opt/kafka/bin/kafka-topics.sh --bootstrap-server broker:9092 \
    --command-config /opt/kafka/config/kraft/admin-client.properties \
    --create \
    --topic cagri-a

/opt/kafka/bin/kafka-topics.sh --bootstrap-server broker:9092 \
    --command-config /opt/kafka/config/kraft/admin-client.properties \
    --list
```

### ACL ADD AND LIST
```bash
/opt/kafka/bin/kafka-acls.sh --bootstrap-server broker:9092 \
    --command-config /opt/kafka/config/kraft/admin-client.properties \
    --add \
    --allow-principal User:client \
    --operation write \
    --topic cagri-a

/opt/kafka/bin/kafka-acls.sh --bootstrap-server broker:9092 \
    --command-config /opt/kafka/config/kraft/admin-client.properties \
    --list
```

### Scrum ACL ADD AND LIST:
```bash
kafka-configs.sh --bootstrap-server broker:9092 \
    --command-config /opt/kafka/config/kraft/admin-client.properties \
    --alter \
    --add-config "SCRAM-SHA-256=[password=cagri3541]" \
    --entity-type users \
    --entity-name client
```

### Consumer / Producer Command
```bash
/opt/kafka/bin/kafka-console-consumer.sh --bootstrap-server broker:9092 --topic cagri-a \
    --consumer.config /opt/kafka/config/kraft/admin-client.properties \
    --from-beginning

/opt/kafka/bin/kafka-console-producer.sh --bootstrap-server broker:9092 --topic cagri-a \
    --producer.config /opt/kafka/config/kraft/admin-client.properties
```