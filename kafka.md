## Install kafka
By far the easiest is a native installation of kafka.
I personally always have some sort of issue when using dockerized kafka's...

Also note: it's easier to do this on a different (virtual)machine, otherwise you need to adjust the kafka config so it will listen to the right IP address! localhost:9092 is often denied.

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

## Start kafka
### tmux
```sh
tmux new -s kafka
```

```sh
bin/zookeeper-server-start.sh config/zookeeper.properties
```

```prefix``` (```C-b```) ```arrow```

```sh
bin/kafka-server-start.sh config/server.properties
```

Take a peek at the advertised hostname, as it is resolved by java.net.InetAddress.getCanonicalHostName().
Make sure it matches your machine's hostname/IP.

Then detach tmux to keep everything running: ```C-b d```

### Attached shell process
```sh
bin/zookeeper-server-start.sh config/zookeeper.properties &&
bin/kafka-server-start.sh config/server.properties &
```
