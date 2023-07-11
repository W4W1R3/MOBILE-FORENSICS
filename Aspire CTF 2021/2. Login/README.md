# Description

Get the correct username and password?

Flag format is: Aspire{username:password}

# Solution

We start with a code review before digging straight into deep thinking, so i used jadx-gui to reverse the application and did a deep probe in the apps MainActivity, found some interesting encoded strings that had been hinted on the challenge description  

![Screenshot](https://github.com/W4W1R3/MOBILE-FORENSICS/blob/main/Aspire%20CTF%202021/2.%20Login/Screenshot_2023-07-11_07-18-29.png)

 This function decodes some embedded Base64 strings and equates them to the strings fed in the UI
