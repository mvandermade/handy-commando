- Download Kafka from http://kafka.apache.org/downloads
- Verify using ```certutils -hashfile <kafkafilename> SHA256```
- Extract to the C drive, otherwise errors occur complaining about the path length.
- in the path of the extracted kafka (C:\kafka) do the following:

- Start Zookeeper (dependency in order to run kafka
```powershell
.\bin\windows\zookeeper-server-start.bat config\zookeeper.properties
```

- In a secoond window:

- Start kafka
```powershell
.\bin\windows\kafka-server-start.bat config\server.properties
```

You will see lots of text, this is normal.

Try to connect to you local kafka now !
