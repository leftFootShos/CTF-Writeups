
##Description:


[Problem source](https://exploit-exercises.com/nebula/level16/)


At this level we have a cgi script that is listening on 1616 port. Just like the
previous levels it has a code injection vulnerability that is pretty obvious
from the very first look, but in this case the script is turning all our input
into uppercase characters, so we can't just simply invoke subshell and execute
$(/bin/getflag)


##Solution



To solve this level, we can use the bash
[escaping](http://tldp.org/LDP/abs/html/escapingsection.html). Since we don't
have enough privilages to create any executable in the path of flag15 user, or
create files at the filesystem root, we'll need to get little creative. Bash
interprets $'\000' values as octal numbers and outputs corresponding ASCII
charaacters. $'\057\164\155\160\057' will be interpreted as `/tmp/`. So we can
create our executable in the /tmp folder and call it EXECUTABLE

	#!/bin/bash

	/bin/getflag/ >/tmp/result

Then after connecting to the server.

	nc 127.0.0.1 1616
	GET /index.cgi?username=$($'\057\164\155\160\057'EXECUTABLE)

This way we can get flag on this account.



##Lessons learned

Bash escape sequences.

Should review CGI protocol.
