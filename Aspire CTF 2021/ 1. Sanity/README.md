# Description

Simple as can be. Obtain the flag from the apk.

[sanitycheck.apk ](sanitycheck.apk)

Generally we have two possible methods to capturing the flag. The simplest would be running strings on the app and using grep to pull out the flag, this would be equal to decompiling the app and looking for the flag in the res or the strings folder.

``` bash
└─$ strings sanitycheck.apk | grep  -oE 'Aspire{.*}' 
Aspire{2c44d2efb924d1908977f5fc4f39fdf5!}
```
The other method would be installing the app and trying to see if we might find the flag, and actually it was showing the flag.
![Screnshot](https://github.com/W4W1R3/MOBILE-FORENSICS/blob/main/Aspire%20CTF%202021/%201.%20Sanity/2.jpg)

Aspire{2c44d2efb924d1908977f5fc4f39fdf5!}
