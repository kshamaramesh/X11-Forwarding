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
On the client side your ~/.ssh/config file have these lines
```

nano -w /etc/ssh/ssh_config

```
```
Host *
  ForwardAgent yes
  ForwardX11 yes
  ```
  
 On your client, connect to your server. Be certain to tell ssh to allow X11 forwarding. I prefer
 
 ```
ssh -X anavs@192.168.1.127
```

[Guide on how to do X11 forwarding in Linux][https://www.addictivetips.com/ubuntu-linux-tips/set-up-x11-forwarding-on-linux/]

