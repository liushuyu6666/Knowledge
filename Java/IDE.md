# Overview

## Load change icon on dependency file.
Depending on your build automation tool of choice, the icon <img align="auto" width="40" height="20" src="img/loadGradleChange.png" alt="Load Gradle Change">  will display.  
Let's use the `Gradle` to explain. Clicking the "Load Gradle changes" button in `IntelliJ IDEA` will trigger a `Gradle` sync. During a `Gradle` sync, `IntelliJ IDEA` will download any new dependencies that have been added to the `Gradle` build script, and update its project settings to reflect any changes that have been made to the `Gradle` configuration. This process ensures that your project is up-to-date with the latest changes and that any new dependencies are available for use in your code.  
**This process is not part of the build itself**, but rather a preparation step that happens before the build.
