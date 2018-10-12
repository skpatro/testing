
# Appium cheatsheet



### Appium capabilities

```java
AppiumDriver<MobileElement> driver = null;
DesiredCapabilities cap;  

cap = new DesiredCapabilities();
  //Android
  cap.setCapability("platformName", "Android");
  cap.setCapability(MobileCapabilityType.AUTOMATION_NAME, AutomationName.ANDROID_UIAUTOMATOR2);
  cap.setCapability("deviceName", "MyDeviceName");
  cap.setCapability("appPackage", "...");
  cap.setCapability("appActivity", "...");
  driver = new AndroidDriver<MobileElement>(new URL("http://127.0.0.1:4723/wd/hub"), cap);
  
  //iOS
  cap.setCapability("platformName", "iOS");
  cap.setCapability("deviceName", "iPhone 8 Plus");
  cap.setCapability("platformVersion", "11.3");
  cap.setCapability("automationName", "XCUITest");
  cap.setCapability("bundleId", "...");
  driver = new IOSDriver<MobileElement>(new URL("http://127.0.0.1:4723/wd/hub"), cap);
  Assert.assertNotNull(driver);
```


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


### Take screenshot

```java
//Takes screenshot and return the path of image
public static String captureScreen(String screenShotName){
		Date date = new Date();
		String fileName = screenShotName+ "_" + dateFormat.format(date);
		String dest = null;
		try {
		File src = ((TakesScreenshot)ThreadLocalWebdriver.getDriver()).getScreenshotAs(OutputType.FILE);
		 dest = System.getProperty("user.dir")+"/TestScreenShots/"+fileName+".png";
		File target = new File(dest);
		FileUtils.copyFile(src, target);
		}catch(Exception e) {
			e.printStackTrace();
		}
		
		return dest;
}
```


### Scroll till text matches

```java
public static void scrollTillText(String text) {
    	((AndroidDriver<MobileElement>) ThreadLocalWebdriver.getDriver()).findElementByAndroidUIAutomator(
    			"new UiScrollable(new UiSelector().scrollable(true).instance(0)).scrollIntoView(new UiSelector().textContains(\""+text+"\").instance(0))");
    }
```


### Scroll up to down

```java
public static void scrollDown() {
    Dimension dimensions = ThreadLocalWebdriver.getDriver().manage().window().getSize();
		Double screenHeightStart = dimensions.getHeight() * 0.5;
		int scrollStart = screenHeightStart.intValue();
		Double screenHeightEnd = dimensions.getHeight() * 0.2;
		int scrollEnd = screenHeightEnd.intValue();
			
		new TouchAction((PerformsTouchActions) ThreadLocalWebdriver.getDriver())
			.press(PointOption.point(0, scrollStart))
			.waitAction(WaitOptions.waitOptions(Duration.ofSeconds(1)))
			.moveTo(PointOption.point(0, scrollEnd))
			.release().perform();
	}
  ```
  
  
  ### Scroll right to left
  
  ```java
  public static void scrollRightToLeft() {
    Dimension dimensions = ThreadLocalWebdriver.getDriver().manage().window().getSize();
    int Anchor = ThreadLocalWebdriver.getDriver().manage().window().getSize().getHeight() / 2;
		Double screenWidthStart = dimensions.getWidth() * 0.8;
		int scrollStart = screenWidthStart.intValue();
		Double screenWidthEnd = dimensions.getWidth() * 0.2;
		int scrollEnd = screenWidthEnd.intValue();
			
		new TouchAction((PerformsTouchActions) ThreadLocalWebdriver.getDriver())
			.press(PointOption.point(scrollStart, Anchor))
			.waitAction(WaitOptions.waitOptions(Duration.ofMillis(1000)))
			.moveTo(PointOption.point(scrollEnd, Anchor))
			.release().perform();
	}
  ```


### Verify toast messages

```java
MobileElement popUpElement = (MobileElement) driver.findElement(MobileBy.AccessibilityId("Make a Popup!"));
  popUpElement.click();
	driver.findElement(By.xpath(".//*[@text='Search']")).click();
	/*Assert.assertNotNull(wait.until(ExpectedConditions.
  presenceOfElementLocated(By.xpath("//*[@text='Clicked popup menu item Search']"))));*/
	Assert.assertNotNull(By.xpath("//*[@text='Clicked popup menu item Search']"));
```
