Connect with

```
> ssh bandit7@bandit.labs.overthewire.org -p 2220
```

The hint says that

`The password for the next level is stored in the file data.txt next to the word millionth`

So this is a classic use-case for `grep`

```
cat data.txt | grep millionth
```

