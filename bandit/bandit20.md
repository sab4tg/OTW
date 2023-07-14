Login to bandit20 as normal:

```
$ ssh bandit20@bandit.labs.overthewire.org -p 2220
```

Again, we're given an executable to run in a certain manner that will somehow give us the key to the next level. It looks like the binary takes a port number via the command line as an argument and tries to connect to localhost on the given port. Sounds like a perfect use case for a netcat listener. 

```
$ nc -l -p 5678
```

Once the listener is listening, we can then run

```
$ ./suconnect 5678
{bandit20 password}
```

and the binary will compare the provided password with the bandit20's password file in `/home/bandit21/.prevpass` (I tried using `strings` on the binary to see if it was hardcoded, unfortunately it was not :( )
