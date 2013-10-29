Tilde Slash Bin - Commands That Make Life Easier
================================================

Some commands that I've made and kept in the ~/bin of every machine I use.

## count

A way to count how many characters you have. It takes every single character
after `count ` and outputs that length. Better than `wc -l` because it'll
include whitespace.

### Example

```
$ count I want to count how long this is
32
```

## git-snapshot

Ever had a feature that's 75% done, but you can't figure out that one critical
bug? You don't want to commit because the code's broken, but you would like to
have a place to resume if you end up breaking more things in the bug hunting
process.

Enter `git-snapshot`. It'll take `-u` or `-p` from `git stash` and give you a
nicely formatted stash (either with your message or a default of `Snapshot:
<branchname> <datetime>`), then immediately apply that stash so you can keep
working.

### Example

```
$ git snapshot
Saved working directory and index state On my-cool-branch: "Snapshot: my-cool-branch Tue Oct 29 14:18:23 MST 2013"
HEAD is now at d3412bc My commit message
# On branch my-cool-branch
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#       modified:   my/cool/changes
#
no changes added to commit (use "git add" and/or "git commit -a")
```

## rep

`rep` is like `watch` in that you can repeat commands every n seconds (`watch`
defaults to 2 seconds, `rep` does not have a default). `rep` is better than
`watch` in some cases because you can see the output of the older commands,
while `watch` will only show you the output of the most recent command.

### Example

```
$ # computer under heavy load due to compiling gcc, I want to monitor load over time
$ rep uptime
 14:26:09 up 354 days, 14 min, 16 users,  load average: 5.40, 5.69, 7.51
...
```
