# Install openjdk portable
download:
https://jdk.java.net/14/
Download windows/x64 zip.
Validate sha256 of the file.

# Unzip
I put it in my user folder. This means it can be found by %USERPROFILE%\jdk-14.0.1

# Register java bin folder to %PATH%
So all programs that need java can find it in the global %PATH%
Go to:
- Right click My PC 
- Click Properties in the menu
- In the left column choose advanced system properties.
- Go to the tab Advanced.
- Click button environment variables.
Add to Uservariables:
```%USERPROFILE%\jdk-14.0.1\bin```
- Note: if you run into trouble calling the command ```java``` check if there are any other java (JRE)'s that are also in the path.
- System path goes before user path, so make sure to check both if you have issues.

# Register JAVA_HOME environment variable
Optional, but lots of programs expect it...
Step by step: 
- Right click My PC 
- Click Properties in the menu
- In the left column choose advanced system properties.
- Go to the tab Advanced.
- Click button environment variables.
- Now in the user variable setting, click button "New..."
- variable name: JAVA_HOME
- Value: %USERPROFILE%\jdk-14.0.1\
