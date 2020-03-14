### Start SSH server
This starts an SSH server at port 22, exposing all accounts to be accessed via username/password. Not recommended on personal machines.
```sh
sudo apt-get install openssh-client openssh-server
sudo service ssh restart
```

### List all public key fingerprints (handy for server)
When you first connect to a server using username/password you SHOULD verify this!
Otherwise there is a risk that your password may be stolen.
```sh
ls /etc/ssh/*.pub | xargs -n1 ssh-keygen -l -f
```

### Show all online ssh sessions
```sh
who
```

### Send shutdown message to client(s)
```sh
wall "to: ALL server is rebooting in 1hr"
echo "john please dont work so hard" | write johndoe
```
