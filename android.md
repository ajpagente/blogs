# Android
## List installed packages
```java
    private static final String TAG = "dummyapp";

    List installedPackages = getApplicationContext().getPackageManager().getInstalledPackages(0);
    for (int i=0; i < installedPackages.size(); i++) {
       Log.i(TAG, installedPackages.get(i).toString());
    }
```
Example output
```
04-03 13:50:25.331 5295-5295/com.msg.dummyapp I/dummyapp: PackageInfo{aa9a805 com.samsung.sec.android.application.csc}
04-03 13:50:25.331 5295-5295/com.msg.dummyapp I/dummyapp: PackageInfo{44c405a com.android.captiveportallogin}
04-03 13:50:25.331 5295-5295/com.msg.dummyapp I/dummyapp: PackageInfo{faf028b com.samsung.android.sconnect}
04-03 13:50:25.331 5295-5295/com.msg.dummyapp I/dummyapp: PackageInfo{2cc9f68 com.samsung.android.coreapps}
04-03 13:50:25.331 5295-5295/com.msg.dummyapp I/dummyapp: PackageInfo{c21bf81 com.gemalto.whitelabel.mpa}
04-03 13:50:25.331 5295-5295/com.msg.dummyapp I/dummyapp: PackageInfo{17e0826 com.singtel.notAnoobie}
04-03 13:50:25.331 5295-5295/com.msg.dummyapp I/dummyapp: PackageInfo{c893c67 com.samsung.android.video}
04-03 13:50:25.331 5295-5295/com.msg.dummyapp I/dummyapp: PackageInfo{5804a14 com.samsung.location}
```
## Custom NDK Path
To build libraries using an older NDK version, set the NDK path in the local.properties file
```
ndk.dir=../../../../AppData/Local/Android/Sdk/android-ndk-r16b
```
## Fixing mips ABI prefix error
You may encounter this error when building a native library:
```
A problem occurred configuring project ':lib'.
> No toolchains found in the NDK toolchains folder for ABI with prefix: mips64el
-linux-android
```
### Cause
This issue may happen if you are using Android Plugin for Gradle 3.0.1 or lower with NDK r17 or higher. That's because older versions of the plugin still include the unsupported ABIs by default when you build per-ABI APKs.
### Fix
One fix is to update to the latest version of the plugin.

In your main build.gradle:
```buildscript {
    repositories {
        jcenter()
        google()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.0.1'
    }
}
```
Replace the classpath to the latest plugin version. E.g. 3.3.2:
```
classpath 'com.android.tools.build:gradle:3.3.2'
```
## Minimum supported Gradle version
Certain versions of the Android Gradle Plugin will require a minimum supported Gradle version. If you have an older Gradle version you may encounter the error below:
```
A problem occurred evaluating project ':lib'.
> Failed to apply plugin [id 'com.android.library']
   > Minimum supported Gradle version is 4.10.1. Current version is 4.1. If usin
g the gradle wrapper, try editing the distributionUrl in <path snip>\gradle\wrapper\gradle-wrapper.properties to gradle-4.10.1-all.z
ip
```
### Fix
Update the distributionUrl to the recommended version:
```
distributionUrl=https\://services.gradle.org/distributions/gradle-4.10.1-all.zip
```
## Could not find aapt2 error
```
Could not resolve all files for configuration ':test:_internal_aapt2_binary'.
> Could not find com.android.tools.build:aapt2:3.3.2-5309881.
  Required by:
      project :test
```
## Fix
Add google() to the main build.gradle
```
buildscript {
    repositories {
        jcenter()
        google()  // Add this
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.3.2'
    }
}

allprojects {
    repositories {
        mavenCentral()
        google() // Add this
    }
}
```
## Could not find trove4j
```
Could not resolve all files for configuration ':xposed:lintClassPath'.
> Could not find org.jetbrains.trove4j:trove4j:20160824.
  Searched in the following locations:
    - https://repo.maven.apache.org/maven2/org/jetbrains/trove4j/trove4j/2016082
4/trove4j-20160824.pom
    - https://repo.maven.apache.org/maven2/org/jetbrains/trove4j/trove4j/2016082
4/trove4j-20160824.jar
    - https://dl.google.com/dl/android/maven2/org/jetbrains/trove4j/trove4j/2016
0824/trove4j-20160824.pom
    - https://dl.google.com/dl/android/maven2/org/jetbrains/trove4j/trove4j/2016
0824/trove4j-20160824.jar
  Required by:
      project :xposed > com.android.tools.lint:lint-gradle:26.3.2 > com.android.
tools.external.com-intellij:intellij-core:26.3.2
```
## Fix
Replace all occurence of **mavenCentral()** in your main build.gradle with **jcenter()**.