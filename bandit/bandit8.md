Connect with

```
> ssh bandit8@bandit.labs.overthewire.org -p 2220
```

This challenge requires you to keep a count of each line in the data.txt file and find the one with count equal to 1. My first inclination for how to solve this is in bash, keeping a count variable and using grep's count flag to keep track of the number of instances of each line. Intuitively, there shouldn't be a faster approach than O(n^2) since each line must be compared with all other lines in the file, so even though this approach is slow, it's a fair baseline without any sort of fancy command line-ism's.

Here is a working sample of the above:

```
for line in $(head data.txt); do count=$(grep $line data.txt -c); if [ $count -eq 1 ]; then echo $line; fi; done
```

This is pretty clunky to write out and requires a working knowledge of bash, so I'm gonna assume there's an easier way to do this using the hinted commands in the bandit8 writeup. Looking at uniq, since it looks like that can be used to identify unique lines with the `-u` command. As it turns out, with a little studying up on the man page, the uniq command really only is helpful here if equivalent lines are adjacent to one another, ie are sorted. So by sorting the output then piping that through uniq, you can get your key to the next station like so.

```
$ sort data.txt | uniq -u
```

I will also add this command runs signficantly faster than my bash solution because comparing every string with its neighbors is O(n). 

- My bash command on an input of 1001 32-bit strings took ~1.5s, while the combination of sort then uniq completes in ~0.005s.
