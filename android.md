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