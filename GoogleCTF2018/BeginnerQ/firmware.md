**PROBLEM - FIRMWARE**

We are given an archive with a file inside it, that can be mounted as a ext4
filesystem. 

**Solution**

At first, we should mount the file.

	sudo mount -t ext4 -o loop challenge.ext4 ./mount_folder

When we mount the fs, the file with the token is in the root directory, but it
starts with `.` so it's hidden from plain `ls`, so we should use `ls -al` to
actually see the file.
	
	.mediapc_backdoor_file.gz


**Token**

CTF{I_kn0W_tH15_Fs}
