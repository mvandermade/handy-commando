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
