# X11-Forwarding
How to forward X over SSH to run graphics applications remotely?


To get X11 forwarding working over ssh, you'll need 3 things in place.

    1.Your client must be set up to forward X11.
    2.Your server must be set up to allow X11 forwarding.
    3.Your server must be able to set up X11 authentication.
    
 First step to check with the server side these steps have been set up
 
```
    nano /etc/ssh/sshd_config
```

```
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost no

```
You may need to SIGHUP sshd so it picks up these changes.
 ```
 cat /var/run/sshd.pid | sudo xargs kill -1

```

On your server, make sure you have xauth installed.
```
which xauth
```
```
/usr/bin/xauth
```

