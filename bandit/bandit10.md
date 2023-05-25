Connect with

```
$ ssh bandit10@bandit.labs.overthewire.org -p 2220
```

This one was fairly straightforward if you know how to use `base64`. We are given that the data in data.txt is base64 encoded, so intuitively all we should need to do is decode it and we should be able to get the password.

```
$ base64 -d data.txt
```
