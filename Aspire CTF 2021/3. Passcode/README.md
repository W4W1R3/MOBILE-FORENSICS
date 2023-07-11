# Description
The user logged in to the application on June 5th. What key did they use?

Flag format is: Aspire{key}
# Files
[Passcode.apk](https://github.com/W4W1R3/MOBILE-FORENSICS/blob/main/Aspire%20CTF%202021/3.%20Passcode/passcode.apk)


# Solution
Code reviewing the MainAcitivity
```bash

    /* JADX INFO: Access modifiers changed from: private */
    public void validate(String passinput) {
        Calendar instance = Calendar.getInstance();
        int password = (int) (Math.pow(instance.get(3) * instance.get(1), 2.0d) % 999983.0d);
        String passwordc = Integer.toString(password);
        if (passinput.equals(passwordc)) {
            Toast.makeText(getApplicationContext(), "Correct Key", 1).show();
        } else {
            Toast.makeText(getApplicationContext(), "Wrong Key Try again", 1).show();
        }
    }
}
```
The code chunk seems to be taking some user input converting it to an integer and equating it to some magic function, well this definitely needed some googling, so i looked up the documentation on class Calendar in java.util.Calendar, got some basic understanding and created the following script to get the passcode.
```bash
import java.util.Calendar;

class passcode{
	int x;
	public static void main(String args[]){
		Calendar instance = Calendar.getInstance();
System.out.println(Integer.toString((int) (Math.pow((double) (instannce.get(3) *instance.get(1)), 2.0d) % 999983.0d))
);
	}
}
```


The user logged in to the application on June 5th. What key did they use?

Seems like we had to change our default date  to June 5th

```bash
└─$ java passcode.java
706009
```
Thus 
# Flag
Aspire{706009}
