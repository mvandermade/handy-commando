# Install openjdk portable
download:
https://jdk.java.net/14/
Download windows/x64 zip.
Validate sha256 of the file.

# Unzip
I put it in my user folder.

# Register java bin folder to %PATH%
So all programs that need java can find it in the global %PATH%
Go to:
System properties (right click "pc" then properties).
Tab Advanced, then click Environment Variables.
Add to Uservariables:
```%USERPROFILE%\jdk-14.0.1\bin```

# Register JAVA_HOME environment variable
Optional, but lots of programs expect it...
Step by step: -Right click My PC > Properties.

Go to the tab Advanced. Click environment variables.
Now in the user variable setting click "New..." and then:
variable name: JAVA_HOME
Value: %USERPROFILE%\jdk-14.0.1\
