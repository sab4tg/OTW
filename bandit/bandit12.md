Connect with

```
$ ssh bandit12@bandit.labs.overthewire.org -p 2220
```

This one took me some manual fooling through unzipping different archives but I guess that is the point of this exercise. I couldn't find a way to automate this without using a bash script, might try to see someone else's solution later to see if there's a faster way.

**Note:** I copied my `data.txt` file into `/tmp/` like the instructions recommended in order to separate out the different stages of decompression into separate files.

`data.txt` is given to us as a hex dump, so first thing we need to do is reverse the hex dump. 

```
$ xxd -r data.txt > stage2
```

From here, you'll notice if you run `file` on the output of the previous command that we're left with a gzip archive. We'll want to rename the output to have a `.gz` extension and then decompress that with the `gzip` (or `gunzip`) utility.

```
$ mv stage2 stage2.gz
$ gunzip -c stage2.gz > stage3
```

From here I used a combination of `file`, `tar`, `gunzip`, and `bzip2` to check the file types of resulting archives, then unzip them according to the type of archive. I could see value in a tool that automates this process (could even be done in a bash script) probably a project for another day.

