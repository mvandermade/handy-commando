# Install

## Prerequisites
Gradle requires JAVA_HOME. To install a JDK that exports these variables take a look at openjdk-windows.

## Download
I downloaded the binaries
https://gradle.org/next-steps/?version=6.5.1&format=bin
Then verified the SHA-256:
https://services.gradle.org/distributions/gradle-6.5.1-bin.zip.sha256
```certutil -hashfile gradle-6.5.1-bin.zip SHA256```

## Install
Extracted to ```%USERPROFILE%\gradle-6.5.1```

## Configure
Add the /bin folder of the extracted data to path. In my case this is %USERPROFILE%\gradle-6.5.1\bin
Therefore I added ```%USERPROFILE%\gradle-6.5.1\bin``` to the user path.
Check the file windows-path-variables.md to check how to to so
