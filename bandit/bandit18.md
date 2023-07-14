bandit19 is quite straightforward to find the key to, once you've circumvented bandit18's bash fence. Once logged into bandit18 using a different shell than bash, you can simply cat `~/readme` and you will obtain the password for bandit19.

```
$ ssh bandit18@bandit.labs.overthewire.org -p 2220 sh
> cat ./readme
```
