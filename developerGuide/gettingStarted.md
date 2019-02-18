# Getting Started

Wecome developer! We're excited to have you build awesome plugins on Figma Plus.

This guide will walk you through the steps to create your first "Hello world" plugin.

## Developer Mode

Developer mode gives you a set of tools to connect your plugin code to Figma. To enable developer mode, select the platform you want to develop in:

<details><summary>Enable developer mode in Desktop app</summary>
<p>

!> Turning on developer mode in your Figma desktop app will set the app's `webSecurity` setting to `false`. This is required for your local server to communicate with the Figma app. By default this shouldn't cause any security concerns if there is no malicious code installed in the app. However if you're uncomfortable with this change we recommend developing your plugin in Chrome.

Open the **Figma Plus Installer** app, then click on the gear in the top right and select **Turn On Dev Mode**. This will prompt you to install the required code into your Figma app. If your app is opened, the installer will warn you before it closes the app.

<img src="images/desktopDevMode.png" width="400">

After restarting the Figma app, open the plugin manager to see a new Developer tab.

<img src="images/devMode.png" width="400">

</p>
</details>

<details><summary>Enable developer mode in Chrome</summary>
<p>

Click on the Figma Plus chrome extension button and toggle on **Developer Mode**. Your page will refresh to apply the setting.

<img src="images/chromeDevMode.png" width="400">

Open the plugin manager to see a new Developer tab.

<img src="images/devMode.png" width="400">

</p>
</details>

## Script Runner

<img src="images/scriptRunner.png" width="600">

To run plugin scripts without setting up a developer environment, open **Script Runner** from the Developer tab and edit your code inside the text box. You can run any Javascript code using the script runner. But for this guide, let's stick with the default demo code:

<!-- prettier-ignore -->
```javascript
figmaPlus.createPluginsMenuItem(				// Create a menu item in the Figma Plus menu.
	'Hello world!',							// Set the menu item's label to "Hello world!"
	() => figmaPlus.showToast('Hello world!')	// When the item is clicked, show a toast that says "Hello world!"
);
```

Hit **Refresh and Run** to run your script after the page refreshes.

You will find a new menu item inside the **Figma Plus** menu called **Hello world!**.

<img src="images/helloWorld.png" width="400">

Click to see a toast pop up at the bottom of your screen.

<img src="images/helloWorldToast.jpg" width="200">

Congratulations! You have created your first Figma Plus plugin!

?> Ready for more? Check out our [API Documentation](api/introduction) or learn how to run plugin code from local files using a [Development Server](developerGuide/devServer#development-server).
