Connect with

```
$ ssh bandit13@bandit.labs.overthewire.org -p 2220
```

This exercise requires you to ssh into localhost as a different user with the ssh key provided. Since we have the ssh key already, we simply use it to ssh onto port 2220

```bash
(bandit13) $ ssh bandit14@localhost -i ./sshkey.private -p 2220
(bandit14) $ cat /etc/bandit_pass/bandit14 
```
