Connect with

```
> ssh bandit5@bandit.labs.overthewire.org -p 2220
```

As we observed in the previous bandit, manually searching through more than a handful of directories and files becomes a pain in the ass real quick. In this case, we have too many files to look through manually, so we'll need to find a way to let bash automate this process. Additionally, the hints section of OTW tells us the password is found in a file that
- is human-readable (I guess that means its ascii)
- 1033 bytes in size
- not executable

Looking at the documentation for `find`, there are a couple of noteworthy flags 

- -maxdepth levels
              Descend at most levels (a non-negative integer) levels of directories below the starting-points.  Us‐
              ing -maxdepth 0 means only apply the tests and actions to the starting-points themselves.
- -size n[cwbkMG]
              File uses less than, more than or exactly n units of space, rounding up.  
- -executable
              Matches files which are executable and directories which are searchable (in a  file  name  resolution
              sense) by the current user.  This takes into account access control lists and other permissions arte‐
              facts which the -perm test ignores.  This test makes use of the access(2) system call, and so can  be
              fooled  by  NFS  servers  which  do UID mapping (or root-squashing), since many systems implement ac‐
              cess(2) in the client's kernel and so cannot make use of the UID  mapping  information  held  on  the
              server.   Because  this  test  is  based only on the result of the access(2) system call, there is no
              guarantee that a file for which this test succeeds can actually be executed.
- ! expr True  if  expr is false.  This character will also usually need protection from interpretation by the
              shell.

So, as it turns out we can craft an expression using the `find` command:

```
> find . -maxdepth 5 -size 1033c ! -executable
```

From the above command we see there is a single file meeting the above criteria that contains our password.

