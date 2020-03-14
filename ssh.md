## Join SSH server
When you first connect to a server using username/password you SHOULD verify this!
Otherwise there is a risk that your password may be stolen.

### Linux
When you have ssh installed on your system:
```
ssh <username>@<SSHserverHostName>
```

### Windows
Use a program like PuTTy: https://www.putty.org.

## While on a Linux system through SSH

### Show all online ssh sessions
```sh
who
```

### Send message to client(s)
```sh
wall "to: ALL server is rebooting in 1hr"
echo "john please dont work so hard" | write johndoe
```

## Start SSH server
### Linux
This starts an SSH server at port 22, exposing all accounts to be accessed via username/password. Not recommended on personal machines.
```sh
sudo apt-get install openssh-client openssh-server
sudo service ssh restart
```

### List all public key fingerprints
When you first connect to a server using username/password you SHOULD verify this!
Otherwise there is a risk that your password may be stolen.
```sh
ls /etc/ssh/*.pub | xargs -n1 ssh-keygen -l -f
```
