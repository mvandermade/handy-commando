# Install

# Why
Useful for making gradle wrappers

## Prerequisites
Gradle requires then environment variable ```JAVA_HOME``` to point to a jdk.
- In my case, the value of JAVA_HOME = ```%USERPROFILE%\gradle-6.5.1\bin```
- To install a JDK, take a look at openjdk-windows.

## Download
- I downloaded the binaries here: https://gradle.org/next-steps/?version=6.5.1&format=bin
- Then verified the SHA-256 with: https://services.gradle.org/distributions/gradle-6.5.1-bin.zip.sha256
- Using ```certutil -hashfile gradle-6.5.1-bin.zip SHA256```

## Install
Extracted using unzip to ```%USERPROFILE%\gradle-6.5.1```

## Configure
- Add the /bin (or \bin on windows) folder of the extracted data to path.
- In my case this is %USERPROFILE%\gradle-6.5.1\bin
- Therefore I added ```%USERPROFILE%\gradle-6.5.1\bin``` to the user path.
- Check the file windows-path-variables.md to check how to to so

# Run
In a new empty folder simply type in the command prompt: ```gradle```.
- You should be greeted by a working gradle !
