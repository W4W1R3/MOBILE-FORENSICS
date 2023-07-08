# Description

Simple as can be. Obtain the flag from the apk.

[sanitycheck.apk ](sanitycheck.apk)

Generally we have two possible approaches to capturing the flag. The simplest would be running strings on the app and using grep to pull out the flag, this would be equal to decompiling the app and looking for the flag in the res or the strings folder.

``` bash
└─$ strings sanitycheck.apk | grep  -oE 'Aspire{.*}' 
Aspire{2c44d2efb924d1908977f5fc4f39fdf5!}
```
