Once logged into bandit17 using the steps from [bandit16.md](https://github.com/sab4tg/OTW/blob/main/bandit/bandit16.md) simply run `diff` to find the difference between the passwords.old and passwords.new files.

```
$ diff passwords.*
```

An annoying aspect of bandit18 is that the `.bashrc` configuration file for bandit18 doesn't let you log in using bash over ssh. Thus, you need to use a different shell. While establishing a login shell is the default behavior for using secure shell, the `ssh` command takes a command parameter to pass along to the receiver in case you want to execute different functionality than a login shell. So we can use the following:

```
$ ssh bandit18@bandit.labs.overthewire.org -p 2220 {command}
```

An easy workaround to the bash fence is simply to use a different shell. `zsh` was my first choice of bash alternative but it didn't look like it was installed on bandit. `sh` comes standard on most \*nix boxes so I resorted to using that. From there you can simply `cat` the readme file in bandit18's home directory and you're off to the races. 

