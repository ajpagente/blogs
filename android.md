# Android
## List installed packages
```java
    private static final String TAG = "dummyapp";

    List installedPackages = getApplicationContext().getPackageManager().getInstalledPackages(0);
    for (int i=0; i < installedPackages.size(); i++) {
       Log.i(TAG, installedPackages.get(i).toString());
    }
```