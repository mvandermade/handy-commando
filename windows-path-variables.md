# Open the settings screen
Go to:
- Right click My PC 
- Click Properties in the menu
- In the left column choose advanced system properties.
- Go to the tab Advanced.
- Click button environment variables.
(- Or through the windows search from the start bar.)

## Register java bin folder to Path
This will allow a console for example to "see" the files in these directories as executables.
- In the user variable setting part: Double click entry "Path" 
- Click button "New"
- Add your variable. For a JDK this could be: ```%USERPROFILE%\jdk-14.0.1\bin```
- System path goes before user path, so make sure to check both if you have issues.

# Register JAVA_HOME environment variable
- In the user variable setting part, click button "New..."
- As example for a JDK this could be:
- Variable name: JAVA_HOME
- Value: ```%USERPROFILE%\jdk-14.0.1\```

# Note:
- If you run into trouble calling the command ```java``` check if there are any other java (JRE)'s that are also in the path.
