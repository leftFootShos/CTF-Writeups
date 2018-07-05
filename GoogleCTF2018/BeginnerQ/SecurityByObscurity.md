**PROBLEM - SECURITY BY OBSCURITY**

In this challenge we have an archive like a Russian doll. An archive that contains an archive that contains an archive and etc. We need to peel off all the layers of compression and get to the final zip archive which is password protected.

**Solution**

We can use the while loop to extract the final file.

	while unzip $(ls | sort | head -n 1); do rm $(ls | sort | tail -n 1); done

	while unxz file.xz; do mv file file.xz; done

	while bunzip2 file.bz; do mv file file.bz; done

	while gunzip file.gz; do mv file file.gz; done

Then we use `zip2john` to turn the zip file into a hash that `john`
can crack. After that we get the password for the final zip archive: `asdf`


**Token**

CTF{CompressionIsNotEncryption}
