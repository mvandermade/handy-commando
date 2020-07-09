Gradle requires JAVA_HOME. To install a JDK that exports these variables take a look at openjdk-windows.

I downloaded the binaries
https://gradle.org/next-steps/?version=6.5.1&format=bin
Then verified the SHA-256:
https://services.gradle.org/distributions/gradle-6.5.1-bin.zip.sha256
```certutil -hashfile gradle-6.5.1-bin.zip SHA256```

Add the /bin folder of the extracted data to path.
In my case I added ```%USERPROFILE%\gradle-6.5.1\bin``` to the user path.
