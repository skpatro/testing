
#ADBCommands


### To invoke an app
```java
adb shell am start -n com.google.android.dialer/.DialtactsActivity
```

### Get the connected device id

```java
adb devices
```

```java
adb kill-server
adb start-server
```

### Install .apk

```java
adb install test.apk

//replace existing
adb install -r test.apk

//install app to sdcard
adb install -s test.apk
```
