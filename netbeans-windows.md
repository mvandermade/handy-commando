## Download Netbeans

# Download

https://netbeans.apache.org/download/nb120/nb120.html
Pick installers: windows-x64.exe edition
Check the SHA512 of the downloaded app.

# Install netbeans
First make sure you have an openJDK folder on your system (or check out windows-openjdk.md).

Then in environment variables, create the variable JAVA_HOME with as value the jdk installation.

Step by step:
-Right click My PC > Properties. 
- Go to the tab Advanced. Click environment variables.
- Now in the user variable setting click "New..." and then:
- variable name: JAVA_HOME
- Value: %USERPROFILE%\jdk-14.0.1\

Now double click the installer and it should work.
