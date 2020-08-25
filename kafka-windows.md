# Install
- Download Kafka from http://kafka.apache.org/downloads
- Verify using ```certutils -hashfile <kafkafilename> SHA256```
- Extract to the C drive, otherwise errors occur complaining about the path length.

# Running
- Open 2 command prompts that are in the the path of the extracted kafka (C:\kafka-version).
- Start Zookeeper in the first command prompt:
```powershell
.\bin\windows\zookeeper-server-start.bat config\zookeeper.properties
```
- In the second command prompt:
```powershell
.\bin\windows\kafka-server-start.bat config\server.properties
```

- You will see lots of scrolling, this is normal.

# Connecting
Try to connect to you local kafka now !
Or use telnet to test the hostname kafka is listening to.
In the lines kafka outputs you'll see to which hostname the kafka-broker is listening to.
It's almost always 9092.

You can test connectivity by telnet (PuTTy) or using a simple consumer in Python etc.

# Commands
## List topics
```powershell
bin\windows\kafka-topics.bat --list --zookeeper localhost:2181
```

## Commandline consumer
```powershell
bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic test
```

## Commandline producer
```powershell
bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic test
```
