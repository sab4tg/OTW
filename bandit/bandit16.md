Connect with

```
$ ssh bandit16@bandit.labs.overthewire.org -p 2220
```

This challenge wants us to do a port scan on a range to find the ones that are open and that have the ssl service is running on them. Easy with netcat.

```
nmap localhost -p 31000-32000 | grep open
```

Using the above command, I found 5 open ports in that range. Easy enough to go through manually. Since the hint says we need to find the open port that speaks ssl, I use the same approach as the previous challenge to submit the bandit15 key to see what they return, like so

```
$ openssl s_client -connect localhost:XXXXX -ign_eof
{paste password acquired in bandit14 challenge}
```

In my case, I found a rsa private key is returned with I submit bandit15's key on port 31790. Saving this key into a private key file in the /tmp directory, I lastly use the private keyfile to log into bandit17. One small issue with this method is that I needed to modify the file permissions of my keyfile to meet OTW's security requirements (it will yell at you if your private key isn't locked down and you try to use it). 

```
chmod 500 /tmp/rsa.private
```

Here, `chmod 500` is telling the operating system to only allow the owner of the file to have RW access to the file, which is the default security level for ssh keys on my own machine. 

Thus I could then log into bandit17 with

```
ssh bandit17@bandit.labs.overthewire.org -p 2220 -i /tmp/rsa.private
```
