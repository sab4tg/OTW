Connect with

```
> ssh bandit4@bandit.labs.overthewire.org -p 2220
```

A bit less trivial. We see a bunch of files beginning with the dash `-`, so the solution for bandit1 comes to mind. Since there are multiple files here, we need to search through each one. Since there's relatively few of them one could check them manually in a reasonable amount of time, though this approach doesn't scale as the size of the directory grows. A one-line bash script automates this process but we still have to eyeball the password

```
> for f in $(ls); do cat ./$f; echo; done
```

We can see in the resulting output the files inside `~/inhere` are mostly binary gibberish, with a single ascii file containing our password.


