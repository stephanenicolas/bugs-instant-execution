# bugs-instant-execution
Sample project to illustrate instant execution bugs in Android projects

Bug 1: https://issuetracker.google.com/issues/148341619
* commit: `d9b42988e6c22c8bd2ca577d9f4ec3c9999c985e`
* command: `./gradlew :app:assembleDebug -Dorg.gradle.unsafe.instant-execution=true`
* Error:
```
Calculating task graph as no instant execution cache is available for tasks: :app:assembleDebug
78 instant execution problems were found, 14 of which seem unique:
  - field 'classes' from type 'java.util.ResourceBundle$RBClassLoader': error writing value of type 'java.util.Vector'
  - field 'nativeLibraries' from type 'java.util.ResourceBundle$RBClassLoader': error writing value of type 'java.util.Vector'
  - field 'urls' from type 'sun.misc.URLClassPath': error writing value of type 'java.util.Stack'
  - field 'permissions' from type 'java.security.ProtectionDomain': error writing value of type 'java.security.Permissions'
  - field 'classes' from type 'sun.misc.Launcher$AppClassLoader': error writing value of type 'java.util.Vector'
  - field 'nativeLibraries' from type 'sun.misc.Launcher$AppClassLoader': error writing value of type 'java.util.Vector'
  - field 'classes' from type 'sun.misc.Launcher$ExtClassLoader': error writing value of type 'java.util.Vector'
  - field 'nativeLibraries' from type 'sun.misc.Launcher$ExtClassLoader': error writing value of type 'java.util.Vector'
  - field 'locale' from type 'java.util.ResourceBundle$CacheKey': error writing value of type 'java.util.Locale'
  - field 'catalogLocale' from type 'java.util.logging.Logger': error writing value of type 'java.util.Locale'
  - field 'classes' from type 'org.gradle.internal.classloader.VisitableURLClassLoader': error writing value of type 'java.util.Vector'
  - field 'nativeLibraries' from type 'org.gradle.internal.classloader.VisitableURLClassLoader': error writing value of type 'java.util.Vector'
  - field 'address' from type 'java.net.SocksSocketImpl': error writing value of type 'java.net.Inet4Address'
  - unknown property: java.lang.StackOverflowError
See the complete report at file:///Users/snicolas/git/BugsInstantExecution/.instant-execution-state/6.2-20200116230058+0000/6pesirgxabwicfqm6vp6kl3r0/instant-execution-report.html
```

"Solution" --> remove the navigation plugin

