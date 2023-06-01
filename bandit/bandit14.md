Connect with

```
$ ssh bandit14@bandit.labs.overthewire.org -p 2220
```

The instructions for bandit 14 tell us we need to `submit the password of the current level on port 30000 to localhost` which sounds an awful lot like a job for netcat. Sure enough, it's one of the hinted commands to use for this challenge. 

```
$ nc localhost 30000
{paste password to previous challenge}
```
