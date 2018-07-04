**PROBLEM - MOAR**

We are given a connection to the server, that provides us with the man page for socat.

**Solution**

At first I though that the flag was embedded in the man page, so I tried to
download the whole man page locally and search for the token. 

	while true;do echo 'd'; sleep 0.01;done | nc https://github.com/leftFootShos/CTF-Writeups >manpage

Unfortunately token was not in the file. Next thing I tried was to execute
external commands from the less pager. After looking through the man page for
_less_ I found out that is supports external commands.
We can use the _!bashcommand_to execute commands inside the less pager, which is
used to view the man pages. If we use _!ls /home/moar_ we can see the file
_disable_dmz.sh_ which contains the flag for the challenge.

