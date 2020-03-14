## Install kafka
By far the easiest is a native installation of kafka.
I personally always have some sort of issue when using dockerized kafka's...

### Install Java
```sh
apt-get install default-jdk
```

### Download and extract Kafka
https://kafka.apache.org/downloads

```sh
wget http://apache.cs.uu.nl/kafka/2.4.1/kafka_2.12-2.4.1.tgz
```

Checksum validate (manually)
```sh
gpg --print-md SHA512 kafka_2.12-2.4.1.tgz
```

Extract kafka at a useful location
```sh
tar -xzf kafka_2.12-2.4.1.tgz
```

## Start kafka as attached process (&)
```sh
bin/zookeeper-server-start.sh config/zookeeper.properties &&
bin/kafka-server-start.sh config/server.properties &
```
