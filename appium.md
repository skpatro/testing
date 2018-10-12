

### WebDriver to AndroidDriver

```java
import io.appium.java_client.android.AndroidDriver;
import org.openqa.selenium.WebDriver;

WebDriver webDriver;
AppiumDriver<MobileElement> appiumDriver;

//...
appiumDriver = new AndroidDriver<MobileElement>(new URL("http://127.0.0.1:4723/wd/hub"), cap);

// appiumdriver to webdriver
webDriver = appiumDriver;

//WebDriver to AndroidDriver
((AndroidDriver<MobileElement>) webDriver).findElementByAndroidUIAutomator(...);
```

