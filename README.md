VMD-Mobile-Test-Automation
Overview:
This repository provides a framework for mobile test automation using Appium, focusing on both Android and iOS platforms. The AppFactory class contains methods for initializing Appium drivers based on the platform (Android/iOS) and environment (local or cloud-based on BrowserStack). The framework is designed to connect to mobile apps, either locally or remotely, and run automated tests.

Features
Cross-platform support: Automates tests for Android and iOS apps.
BrowserStack Integration: Supports cloud testing on BrowserStack for both Android and iOS.
Local Device Testing: Allows running tests on local emulators/simulators for Android and iOS.
Appium Driver Setup: Configures Appium drivers for different platforms with specific capabilities.
Getting Started
To use this framework for mobile test automation, follow the instructions below to set up and run the tests.

Prerequisites
Appium: Install Appium to interact with mobile devices.
Java: Ensure Java is installed to run the framework.
BrowserStack Account (optional): If you are using BrowserStack for cloud testing, you need a BrowserStack account with the credentials.
Device/Simulator/Emulator: Either have a physical device or use a simulator/emulator for testing.
Dependencies
Appium: io.appium:java-client:7.x.x
Java SDK
BrowserStack Account (for cloud testing)
Setup
1. Clone the repository
bash
Copy code
git clone https://github.com/yadambayev/VMD-Mobile-Test-Automation.git
cd VMD-Mobile-Test-Automation
2. Install dependencies
Make sure to install the required dependencies, such as Appium and Appium drivers for the devices (Android/iOS).

bash
Copy code
npm install -g appium
3. Configure Capabilities
Local Testing: Set AppData.isCloud to "false" in the AppData configuration to use local emulators/simulators.
Cloud Testing (BrowserStack): Set AppData.isCloud to "true", and provide your BrowserStack credentials in the android-caps.json or ios-caps.json file.
4. Add Device Details
Update the android-caps.json and ios-caps.json files with the correct device details (e.g., device name, platform version, app package, etc.).
If using BrowserStack, include your username, access key, and appium version in these JSON files.
5. Running Tests
You can run tests by calling the launchApp() method from the AppFactory class. This method will automatically select the platform and connect to the app on either an Android or iOS device.

Example:
java
Copy code
AppFactory.launchApp();
This will:

Set up the Appium driver based on the platform (Android/iOS).
Connect to the app either locally or on BrowserStack (depending on the configuration).
Launch the app for automated testing.
Example Platform Configuration:
json
Copy code
{
    "deviceName": "iPhone 15",
    "platformVersion": "17.2",
    "bundleId": "com.demo1.mydemoapp.rn",
    "browserStackURL": "bs://fe3d1aca9849e845f98a4f7d6482407d143d5048",
    "userName": "your_browserstack_username",
    "accessKey": "your_browserstack_access_key",
    "appiumVersion": "2.4.1"
}
Code Explanation
AppFactory.java
The core functionality of this project is encapsulated in the AppFactory class. Here's an overview of the key methods:

getBrowserstackOptions():

Retrieves default BrowserStack configuration options like username, access key, and Appium version.
setBrowserstackOptions():

Sets custom BrowserStack configuration options for cloud testing.
android_connectToApp():

Sets up the Android Appium driver. It checks if the test is running locally or on BrowserStack and configures the driver accordingly.
ios_connectToApp():

Similar to the Android configuration, but for iOS devices. It sets up the iOS Appium driver with the correct capabilities.
launchApp():

Main entry point for launching the mobile app. It selects the platform (iOS or Android) and calls the respective connection method (android_connectToApp() or ios_connectToApp()).
Appium Drivers
Android Driver: Uses the AndroidDriver with UiAutomator2Options for local and cloud-based testing.
iOS Driver: Uses the IOSDriver with XCUITestOptions for local and cloud-based testing.
Troubleshooting
Error: Could not connect to the Appium server
Ensure that Appium server is running (appium command).
Check the device/emulator configuration in the android-caps.json or ios-caps.json files.
BrowserStack Authentication Failure
Double-check your userName and accessKey in the android-caps.json and ios-caps.json files.
