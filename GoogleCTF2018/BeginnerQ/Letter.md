**LETTER**

In this challenge we are presented with a PDF file, which contains a login and a
password, but both of them are blacked out.

**Solution**

*TLDR*

__Poppler__ utility library contains a program called _pdftotext_, we can use
this program to extract the information we need.


First thing I tried was to use _strings_ program on the pdf file, but
unfortunately text in pdf is, most likely, encoded so it didn't really return
anything interesting. After looking around for ways to extract text from pdf
file, I found __Poppler__ package. It is a backbone for rendering pdf for many
open source pdf viewers. It also contains a program called _pdftotext_ which we
can use to extract the flag from the file.

**Lessons Learned**

This challenge is a good place to start diving deeper into the pdf file format,
and also explore the __Poppler__ package, which looks like an important piece in
pdf rendering in the linux environment.

**PDF**


