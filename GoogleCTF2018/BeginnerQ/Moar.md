**PROBLEM - MOAR**

We are given a connection to the server, that serves man pages through the network.

**Solution**

Manual is served thorugh the program **less**, which means we can use commands
to query for additional data.

At first I though that the flag was embedded in the man page, so I've 
downloaded the whole man page locally and searched thorugh for the token.

	while true;do echo 'd'; sleep 0.01;done | nc https://github.com/leftFootShos/CTF-Writeups >manpage

Unfortunately token was not in the file. Next thing I tried was to execute
external commands from the **less** pager. After looking through the man page for
**less** I found out that it supports execution of  external commands.
We can use the _!bashcommand_to execute commands
If we use _!ls /home/moar_ we can see the file
_disable_dmz.sh_ which contains the flag for the challenge.


**Token**

	CTF{SOmething-CATastr0phic}
