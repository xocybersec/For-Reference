`-type` will display files, directories, symlinks, named pipes, sockets, and more

```
d = directory      l = symlink
f = file           s = socket
p = named pipe     b = block (buffered) special
c = character (unbuffered) special
```

`-name` will search for extensions <br>
*NOTE: Use `2>/dev/null` to silence permission errors (sends error messages to /dev/null)*
```
$ find /tmp -name "foo.txt"  2>/dev/null     Find a file a called foo.txt in /tmp
$ find /tmp -iname "foo.txt"                 Find a file (case insensitive) called foo.txt in /tmp
$ find /tmp -name "foo*"                     Find a file starting with the substring foo
$ find /tmp -regex ".*f.*t"                  Find regex pattern (regex must include the full path)
```

`-mtime` finds files by age
```
-mtime -7               Modified within the last 7 days
-mtime +1 -mtime -7     Modified more than 1 day ago, but no more than 7
-daystart               Start from today rather than from 24 hours ago
```

Folders and files that can be written to or executed from:
```
$ find / -writable -type d 2>/dev/null   : Find world-writeable folders
$ find / -perm -222 -type d 2>/dev/null  : Find world-writeable folders
$ find / -perm -o w -type d 2>/dev/null  : Find world-writeable folders
$ find / -perm -o x -type d 2>/dev/null  : Find world-executable folders
```

Find development tools and supported languages:
```
$ find / -name perl*
$ find / -name python*
$ find / -name gcc*
```

Find specific file permissions:
```
$ find / -perm -u=s -type f 2>/dev/null
# Find files with the SUID bit, which allows us to run the file with a higher privilege level than the current user.

$ find / -type f -user <username> 2>/dev/null
# Find files owned by user
```

Find all hidden files:
```
find / -type f -iname ".*" -ls 2>/dev/null
```

Execute commands with find:
```
$ find /directory/name -exec <command> \;
$ find /root -exec cat "/root/root.txt" \;  : Read a file called root.txt in /root directory


