Connect with

```
$ ssh bandit15@bandit.labs.overthewire.org -p 2220
```

This challenge makes use of openssl to connect to 

```
$ openssl s_client -connect localhost:30001 -ign_eof
{paste password acquired in bandit14 challenge}
```
