Connect with

```
> ssh bandit9@bandit.labs.overthewire.org -p 2220
```

I didn't want to cheat this time by using bash, and moreover I didn't have to since this appears to be a textbook use-case for `strings`. This gets you all of the human readable strings in a file (works with unicode and ascii) and using the knowledge that the target is preceded by several "=" we can pipe the output of running strings through grep to search for this character.  

```
$ strings data.txt | grep "="
```
