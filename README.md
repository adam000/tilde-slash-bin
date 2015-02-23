Tilde Slash Bin - Commands That Make Life Easier
================================================

Some commands that I've made and kept in the `~/bin` of every machine I use.

These bash utility scripts are not one-size-fits-all, so I would recommend
symlinking the useful scripts from your repo directory to `~/bin` instead of
cloning into `~/bin`.

I've used these scripts on OS X, Ubuntu, and CentOS.

This code is released under the MIT license. See LICENSE for details.

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

## mvln

Ever put something in a directory, then realized it needs to be somewhere else,
but you still want to symlink to the current directory? `mvln` does this in one
fluid step.

### Example

```
$ mvln ~/git/my-awesome-command /usr/local/bin/my-awesome-command

$ ll ~/git/my-awesome-command
lrwxr-xr-x  1 username  root  3 Oct 29 16:18 /Users/username/git/my-awesome-command -> /usr/local/bin/my-awesome-command
```

## pingg

Ping google.com. Keep trying to ping it as long as it's failing. Optionally,
supply a parameter to specify how often `ping` should be pinging (the number is
passed as the argument to the `-i` parameter).

Useful if you want to check connectivity to the Internet.

### Example

```
$ pingg
PING google.com (74.125.239.5): 56 data bytes
64 bytes from 74.125.239.5: icmp_seq=0 ttl=58 time=5.394 ms
^C
--- google.com ping statistics ---
1 packets transmitted, 1 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 5.394/5.394/5.394/0.000 ms
```

## rep

`rep` is like `watch` in that you can repeat commands every n seconds (`watch`
defaults to 2 seconds, `rep` does not have a default). `rep` is better than
`watch` in some cases because you can see the output of the older commands,
while `watch` will only show you the output of the most recent command.

While this does work with functions, it fails with aliases due to [how bash
works](http://stackoverflow.com/a/11136867/211176). Convert aliases to functions
if you need to use them with `rep`.

### Example

```
$ # computer under heavy load due to compiling gcc, I want to monitor load over time
$ rep 1 uptime
 14:26:09 up 354 days, 14 min, 16 users,  load average: 5.40, 5.69, 7.51
 14:26:10 up 354 days, 14 min, 16 users,  load average: 5.45, 5.70, 7.48
...
```

## git-supa-clean

`git-supa-clean` is when you want your working directory to be really, really
clean. It removes staged, unstaged, and untracked changes to leave your code
spotless.

### Example

```
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   foo

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   bar

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        baz
$ git supa-clean
$ git status
On branch master
nothing to commit, working directory clean
```

## git-supa-quickfix

`git-supa-quickfix` adds all changes, ammends the latest commit, and force
pushes that commit. Sometimes you accidentally typo something and realize it
just moments after. Just supa-quickfix it!

### Example

*tbd*

## git-blep

`git-blep` does a git blame on a git grep! How cool!

### Example

*tbd*

## git-stash-staged

Sometimes it's easier to `git add` some files or `git add -p` some particular
changes than to `git stash save -p` those changes. If you already have some
changes staged and you want to stash them instead of committing, this is the
tool for you!

### Example

*tbd*
