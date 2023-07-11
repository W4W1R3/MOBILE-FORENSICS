# Description
Preloaded Databases Leak Secrets?
# Files
[Sqlitedb.apk](https://github.com/W4W1R3/MOBILE-FORENSICS/blob/main/Aspire%20CTF%202021/4.%20Preload/sqlitedb.apk)
# Solution
The app name itself was much of a description, so i did some **CODE REVIEW**
![Screeenshot](https://github.com/W4W1R3/MOBILE-FORENSICS/blob/main/Aspire%20CTF%202021/4.%20Preload/Screenshot_2023-07-11_08-35-19.png)

So you could either decompile the app and extract the database, or just install the app and pull the database from the app’s sandbox.

Decompiling is easier so i went with the method
```bash
└─$ apktool d sqlitedb.apk 
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
I: Using Apktool 2.7.0-dirty on sqlitedb.apk
I: Loading resource table...
I: Decoding AndroidManifest.xml with resources...
I: Loading resource table from file: /home/billie/.local/share/apktool/framework/1.apk
I: Regular manifest package...
I: Decoding file-resources...
I: Decoding values */* XMLs...
I: Baksmaling classes.dex...
I: Baksmaling classes2.dex...
I: Baksmaling classes3.dex...
I: Copying assets and libs...
I: Copying unknown files...
I: Copying original files...
  ```
Navigating the database using SQLite
```bash
└─$ sqlite3                     
SQLite version 3.40.1 2022-12-28 14:03:47
Enter ".help" for usage hints.
Connected to a transient in-memory database.
Use ".open FILENAME" to reopen on a persistent database.
sqlite> .open aspire1.sqlite3
sqlite> .tables
aspire     flag       passwords
sqlite> SELECT * FROM aspire;
aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g/dj1kUXc0dzlXZ1hjUQ==|aXQgaXMgbmV2ZXIgdGhhdCBlYXN5|cGFzdGViaW4gaXMgYXdlc29tZQo=|ZXhhbXBsZSBmbGFnIHBhc3N3b3JkPSAxMjM0CnBhc3RlYmluLmNvbS8xMjM0Cg==
sqlite> ^Z
zsh: suspended  sqlite3
                                                                                                                                    
┌[~/…/Aspire CTF 2021/sqlitedb/assets/databases]
└─$ echo 'ZXhhbXBsZSBmbGFnIHBhc3N3b3JkPSAxMjM0CnBhc3RlYmluLmNvbS8xMjM0Cg==' | base64 -d
example flag password= 1234
pastebin.com/1234
```
Got some hints
![Screenshot](https://github.com/W4W1R3/MOBILE-FORENSICS/blob/main/Aspire%20CTF%202021/4.%20Preload/1%20ZrdaBlnDcVMwi7KZRUPHjA.webp)
