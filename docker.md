Play around with Python in a container (with pip)
```
docker run -it python:rc-slim-buster
```

Play around in a terminal with Python installed
```
docker run -it python:rc-slim-buster bash
```

Persist some data through a mounted volume when using the Python container
```
docker run -it -v <LOCALPATH>:<CONTAINERPATH> python:rc-slim-buster bash
```

Show all containers and their id's
```
docker ps
```

Attach terminal to running container (if the container has bash installed)
```
docker exec -it <container-id> bash
```
