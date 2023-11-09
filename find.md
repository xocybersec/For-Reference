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
