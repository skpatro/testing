
#Android_iOS_SimulatorCommands

### Prerequisite for emulator & adb commands

```java
//Setup below env setups, note - android sdk should be downloaded through android studio
export ANDROID_HOME=/Users/MacUserName/Library/Android/sdk
export PATH=${PATH}:$ANDROID_HOME/emulator:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools
```

### To invoke an app
```java
adb shell am start -n com.google.android.dialer/.DialtactsActivity
```

### Get the connected device id

```java
adb devices

//If device is connected, but not listing, then follow below commands
adb kill-server
adb start-server
adb devices
```

### Install .apk

```java
adb install test.apk

//replace existing
adb install -r test.apk

//install app to sdcard
adb install -s test.apk
```

  
### Launch android simulator cmd

```java
//get the avd names
emulator -list-avds
//launch the simulator with avd name
emulator <deviceName>
```

  
### Open iOS simulator cmd

```java
xcrun simctl boot <UDID>
```

  
### Get iOS app bundleID

```java
//If you build the ios app source code in xcode, you can get the .app file under   
// /Users/[MacUserName]/Library/Developer/Xcode/DerivedData/[AppName_xxxxxx]/Build/Products/Debug-iphonesimulator/[appName].app

osascript -e 'id of app "/path/of/ios/appName.app"'
```
   
   
### Get simulator device ID cmd

```java
//for android
adb devices

//for iOS
xcrun simctl list devices | grep '(Booted)'
```
