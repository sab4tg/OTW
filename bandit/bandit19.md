Log into bandit19 like so, using the password in bandit18's `readme` file:	
```
$ ssh bandit19@bandit.labs.overthewire.org -p 2220
```

The instructions for bandit19 are to use the executable provided in the home directory to execute a command to read the contents of a file in `/etc/bandit_pass/`. Upon investigating what's in that directory, we observe several regular files with annoyingly locked down permissions; password files named after their respective owners and only viewable by their respective owners.

As the name implies, the given executable sets your uid temporarily to be that of bandit20, which we can then use to `cat` the contents of /etc/bandit_pass/bandit20.

```
bandit19@bandit $ ./bandit20-do cat /etc/bandit_pass/bandit20 
```
