Connect with

```
$ ssh bandit11@bandit.labs.overthewire.org -p 2220
```

This one took me a couple tries. First I had to figure out which command to use of the ones in the hint they provide:
- grep
- sort
- uniq
- strings
- base64
- tr
- tar
- gzip
- bzip2
- xxd

We're transforming the data in data.txt per-character, so intuitively it seems like we should use `tr` which is a data translation capability. I admittedly had no familiarity with this tool going into this challenge so I had to do a bit of trial and error to get the syntax down, but basically all you're doing is mapping a sequence of strings to another sequence of different strings, and `tr` is smart enough to line up the translations in sequence.

Because all we're doing is rotating characters by 13 positions, this effectively translates to a mapping from the nth character in the set of [a-m] to the nth character in the set of [n-z], and visa versa. Same goes for capital letters.

```
$ cat data.txt | tr [a-m,n-z,A-M,N-Z] [n-z,a-m,N-Z,A-M]
```
