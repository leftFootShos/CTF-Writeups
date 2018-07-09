**PROBLEM - Media-md**

We are given a python script and an URL that serves the script over from the 
network. By examining the script, it becomes clear that the program reads and
writes from the sqlite database, so SQL injection is the most likely attack
vector that we can use.

**Solution**

The program uses `string.format()` method to concatenate user provided strings
with the sql command, this gives us the opportunity to inject custom SQL. If
we chose the _add_song_ option we can use single quotes in our name, as they
are not escaped.
	`' UNION SELECT oauth_token, 2 in oauth_tokens --`

**Token**

	CTF{fridge_cast_oauth_token_cahn4Quo}
