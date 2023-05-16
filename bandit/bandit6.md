Connect with

```
> ssh bandit6@bandit.labs.overthewire.org -p 2220
```

Same kinda deal as the previous bandit - we need to use a find expression that matches the given constraints.

As we observed in the previous bandit, manually searching through more than a handful of directories and files becomes a pain in the ass real quick. In this case, we have too many files to look through manually, so we'll need to find a way to let bash automate this process. Additionally, the hints section of OTW tells us the password is found in a file that
- is somewhere on the server...
- is owned by user bandit7
- is owned by group bandit6
- is 33 bytes in size

After doing some more find-Frankenstein using the find manual, I came up with the following:

```
> find / -maxdepth 10 -user bandit7 -group bandit6 -size 33c 
```

From the above command we see there is a single file meeting the above criteria that contains our password.

