**PROBLEM - OCR**

We are given a screenshot of an email, but the text is all gibberish. From the 
challenge description it's obvious that the encryption used is Caesars cypher, 
so only thing left to do is to guess the shift number.

**Solution**

Before doing anything else, at first we can guess the shift number of the
cypher. First word in the email is most likely _Dear_. If we take **7** as the
shift number, __Wxtk__ is mapped to __Dear__, just as we expected. So the shift
number is **7**.

As the name suggests, we have to use some kind of Optical Character Recognition 
(OCR) system to digitalize the raster image and extract the information, but in 
this case it's not really that necessary. If we skim the email, we can see a
segment of text: __VMY{gibberish}__, this snippet looks suspiciously like the
token that we are looking for, so we can just write this snippet out and apply
the shift. We get __CTF{caesarcipherisasubstitutioncipher}__, which is the key
of this challenge.
