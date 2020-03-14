### List all public key fingerprints (handy for server)
```bash
ls /etc/ssh/*.pub | xargs -n1 ssh-keygen -l -f
```
