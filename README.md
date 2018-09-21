# CosmiPasswordDecoder

Cosmi is a publisher of Fine Shovelware and around 1997 they released some 
CDs of all their software, so they didn't have to master multiple CDs
for each of their programs. You had to enter a password to decode the program
you wanted to install, but since the passwords are included in the setup.ini
file in a simply encoded format, you can easily extract them with the this 
tool.

This is reverse engineered out of the original setup program. You can see a 
rambling twitter thread about this here: 
https://twitter.com/Foone/status/1023422361729609728

# Usage

```
python3 decode.py
```

Just run python3 decode.py, after copying setup.ini into the same folder.
it'll print out the passwords and also create results.csv containing them.

Note: You can't run it from the base of the CD itself, cause it tries to write
a file to the current directory. Sorry. I should fix that someday. 

# Password algorithm

Each byte of the password is XORed with the key byte.
The key byte starts at 0x80, and is incremented by one for each letter of 
the password. 
At the end, throw away the first 5 characters. 

The coding of the setup.ini file seems to be Windows-1252.

# Example ISOs to run this on:

* https://archive.org/details/MMCD450
* https://archive.org/details/MASCD35JJP
* https://archive.org/details/CosmiMultiMediaCDGreetingCardMagicCosmiCorporationSJ1101961996