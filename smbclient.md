# smbclient

```
$ smbclient -L <target_IP>
# find out what the shares on the target machine

*NOTE: you can also use the enum4linux tool to find smb shares*
```

# In the shell, the '\\' has special meaning. Here are work arounds.
```
$ smbclient &apos;\\machine_name\share_name&apos; (1/1)
# quote the service name

$ smbclient /\/\machine_name/\share_name (2/2)
# Try to escape each '\'

$ smbclient \\\\machine_name\\share_name (3/3)
# Using too few '\' will result in an error. Try this to remedy.

$ smbclient \\\\machine_name\\share_name -U username
# When accessing with a username
```
