# UI Functions

Use these functions to set up your plugin and insert menu items for users to interact with. Plugins are recommended to have at least a Plugins menu item, and optionally add a context menu item and/or keyboard shortcut if necessary.

## createPluginsMenuItem

Create an item in the **Figma Plus** menu.

<img src="images/pluginsMenu.png" width="400">

<!-- prettier-ignore -->
```javascript
figmaPlus.createPluginsMenuItem(
	itemLabel,
	triggerFunction,
	condition,
	shortcut,
	submenuItems
);
```

- **itemLabel** (`String`): The label of the menu item to be added.
- **triggerFunction** (`Function`): The function to trigger when the menu item is clicked. If there are sub-menus, this trigger function will not be runned on click.
- **condition (optional)** (`Function`): Condition that needs to pass for the item to show in the menu. Menu item will only show when this condition function returns `true`. Pass `null` if no condition is needed.
- **shortcut (optional)** (`Shortcut`): Pass in a keyboard shortcut object to show it alongside the label. Remember to use `createKeyboardShortcut` to actually attach the command to a keyboard shortcut event. Pass `null` if no shortcut is needed to be displayed.

<details><summary>Click to see the Shortcut object format</summary>
<p>

```
{
	mac : {
		control: <boolean>,
		option: <boolean>,
		shift: <boolean>,
		command: <boolean>,
		key: <String>
	},
	windows: {
		control: <boolean>,
		alt: <boolean>,
		shift: <boolean>,
		key: <String>
	}
}
```

</p>
</details>

- **submenuItems (optional)** (`Array`): Pass in an array of `submenuItem` objects to create sub-menu items branching off the menu item. Pass `null` if no sub-menu is needed.

<details><summary>Click to see the submenuItems object format</summary>
<p>

```
{
	itemLabel: <String>,
	triggerFunction: <Function>,
	condition: <Function> (optional),
	shortcut: <Shortcut> (optional)
}
```

</p>
</details>

<!-- prettier-ignore -->
```javascript
// Example code for creating a simple  Plugins menu item:
figmaPlus.createPluginsMenuItem(
	'Hello world!',
	() => alert('Hello world!')
);

// Example code for creating a simple Plugins menu item with sub-menu:
figmaPlus.createPluginsMenuItem(
	'Hello world!',
	null,
	null,
	null,
	[
		{
			itemLabel: 'Hello',
			triggerFunction: () => alert('Hello')
		},
		{
			itemLabel: 'World',
			triggerFunction: () => alert('World')
		}
	]
);
```

## createContextMenuItem

Create an item in a specific context menu. Here are the supported menu types (Click to see image):

<details>
	<summary><b>Canvas</b></summary>
	<img src="images/canvasMenu.jpg" width="400">

<!-- prettier-ignore -->
```javascript
figmaPlus.createContextMenuItem.Canvas(
	itemLabel,
	triggerFunction,
	condition,
	shortcut,
	submenuItems
);
```

</details>

<details>
	<summary><b>Selection</b></summary>
	<img src="images/selectionMenu.png" width="600">

<!-- prettier-ignore -->
```javascript
figmaPlus.createContextMenuItem.Selection(
	itemLabel,
	triggerFunction,
	condition,
	shortcut,
	submenuItems
);
```

</details>

<details>
	<summary><b>Page</b></summary>
	<img src="images/pageMenu.jpg" width="500">

<!-- prettier-ignore -->
```javascript
figmaPlus.createContextMenuItem.Page(
	itemLabel,
	triggerFunction,
	condition,
	shortcut,
	submenuItems
);
```

</details>

<details>
	<summary><b>Filename</b></summary>
	<img src="images/filenameMenu.jpg" width="350">

<!-- prettier-ignore -->
```javascript
figmaPlus.createContextMenuItem.Filename(
	itemLabel,
	triggerFunction,
	condition,
	shortcut,
	submenuItems
);
```

</details>

<details>
	<summary><b>Version</b></summary>
	<img src="images/versionMenu.jpg" width="300">

<!-- prettier-ignore -->
```javascript
figmaPlus.createContextMenuItem.Version(
	itemLabel,
	triggerFunction,
	condition,
	shortcut,
	submenuItems
);
```

</details>

<details>
	<summary><b>File</b></summary>
	<img src="images/fileMenu.jpg" width="450">

<!-- prettier-ignore -->
```javascript
figmaPlus.createContextMenuItem.File(
	itemLabel,
	triggerFunction,
	condition,
	shortcut,
	submenuItems
);
```

</details>

Use `figmaPlus.createContextMenuItem.` + **Menu Type** to create an item in the given type of menu.

For example, to create a Canvas menu item:

<!-- prettier-ignore -->
```javascript
figmaPlus.createContextMenuItem.Canvas(
	itemLabel,
	triggerFunction,
	condition,
	shortcut,
	submenuItems
);
```

- **itemLabel** (`String`): The label of the menu item to be added.
- **triggerFunction** (`Function`): The function to trigger when the menu item is clicked. If there are sub-menus, this trigger function will not be runned on click.
- **condition (optional)** (`Function`): Condition that needs to pass for the item to show in the menu. Menu item will only show when this condition function returns `true`. Pass `null` if no condition is needed. Default: `true`
- **shortcut (optional)** (`Shortcut`): Pass in a keyboard shortcut object to show it alongside the label. Remember to use `createKeyboardShortcut` to actually attach the command to a keyboard shortcut event. Pass `null` if no shortcut is needed to be displayed.

<details><summary>Click to see the Shortcut object format</summary>
<p>

```
{
	mac : {
		control: <boolean>,
		option: <boolean>,
		shift: <boolean>,
		command: <boolean>,
		key: <String>
	},
	windows: {
		control: <boolean>,
		alt: <boolean>,
		shift: <boolean>,
		key: <String>
	}
}
```

</p>
</details>

- **submenuItems (optional)** (`Array`): Pass in an array of `submenuItem` objects to create sub-menu items branching off the menu item. Pass `null` if no sub-menu is needed.

<details><summary>Click to see the submenuItems object format</summary>
<p>

```
{
	itemLabel: <String>,
	triggerFunction: <Function>,
	condition: <Function> (optional),
	shortcut: <Shortcut> (optional)
}
```

</p>
</details>

<!-- prettier-ignore -->
```javascript
// Example code for creating a simple Canvas menu item:
figmaPlus.createContextMenuItem.Canvas(
	'Hello world!',
	() => alert('Hello world!')
);

// Example code for creating a simple Canvas menu item with sub-menu:
figmaPlus.createContextMenuItem.Canvas(
	'Hello world!',
	null,
	null,
	null,
	[
		{
			itemLabel: 'Hello',
			triggerFunction: () => alert('Hello')
		},
		{
			itemLabel: 'World',
			triggerFunction: () => alert('World')
		}
	]
);
```

## createKeyboardShortcut

Attach a function to a keyboard shortcut. Remember to include a shortcut hint in the Plugins menu/context menu item (See above).

<!-- prettier-ignore -->
```javascript
figmaPlus.createKeyboardShortcut(shortcut, triggerFunction, condition);
```

- **shortcut** (`Shortcut`): An object defining the keyboard shortcut for both Mac and Windows.

<details><summary>Click to see the Shortcut object format</summary>
<p>

```
{
	mac : {
		control: <boolean>,
		option: <boolean>,
		shift: <boolean>,
		command: <boolean>,
		key: <String>
	},
	windows: {
		control: <boolean>,
		alt: <boolean>,
		shift: <boolean>,
		key: <String>
	}
}
```

</p>
</details>

- **triggerFunction** (`Function`): The function to trigger when the shortcut is pressed.
- **condition (optional)** (`Funtion`): Condition that needs to pass for the shortcut to register. The triggerFunction will only run when this condition function returns `true`. Pass `null` if no condition is needed. Default: `true`

```javascript
// Example code for creating a simple keyboard shortcut:
figmaPlus.createKeyboardShortcut(
	{
		mac: {
			command: true,
			shift: true,
			key: 'H'
		},
		windows: {
			control: true,
			shift: true,
			key: 'H'
		}
	},
	() => alert('Hello world!')
);
```

## showUI

Show a Figma styled modal where you can attach your UI onto. Providing a `tabs` array would create a modal with tabs.

<img src="images/modal.jpg" width="400"> <img src="images/tabbedModal.jpg" width="400">

```javascript
figmaPlus.showUI(modalTitle, callback, width, height, positionX, positionY, overlay, includePadding, tabs);
```

- **modalTitle** (`String`): The title to show on the modal header.
- **callback** (`Function`): The callback function that returns after the modal is opened. `modalElement` is passed as an argument to allow UI attachment (See example below).
- **width (optional)** (`Number`): Width of the modal in px. Default: `300`
- **height (optional)** (`Number || String`): Height of the modal in px or 'auto' (Height of the inner elements). Default: `auto`
- **positionX (optional)** (`Number`): Horizontal position in % relative to the screen, ranges from 0 to 1. Default: `0.5` (Center of the screen)
- **positionY (optional)** (`Number`): Vertical position in % relative to the screen, ranges from 0 to 1. Default: `0.5` (Center of the screen)
- **overlay (optional)** (`Boolean`): Whether the modal has a dark overlay background. Default: `false`
- **includePadding (optional)** (`Boolean`): Whether to include the default padding (`padding: 12px`) around the modal content. Default: `true`
- **tabs (optional)** (`Array`): Array of tab titles in `String`. E.g. `['One', 'Two', 'Three']`

<!-- prettier-ignore -->
```javascript
// Attaching UI using pure HTML/Javascript
figmaPlus.showUI(
	'Hello world',
	(modalElement) => {
		const UI = document.createElement('div');
		UI.innerHTML = '<h1>Hello world</h1>';
		modalElement.parentNode.replaceChild(UI, modalElement);
	}
);

// Attaching UI using React (React and ReactDOM are available in figmaPlus.React and figmaPlus.ReactDOM)
figmaPlus.showUI(
	'Hello world',
	(modalElement) => {
		figmaPlus.ReactDOM.render('Hello, world!', modalElement);
	}
);

// Attaching UI using Vue (Vue is available in figmaPlus.Vue)
figmaPlus.showUI(
	'Hello world',
	(modalElement) => {
		new figmaPlus.Vue({
			el: modalElement,
			template: `<h1>Hello world</h1>`
		})
	}
);

// Attaching multiple UI screens to different tabs using Vue
figmaPlus.showUI(
	'Hello world',
	(modalElement, modalElement2) => {
		new figmaPlus.Vue({
			el: modalElement,
			template: `<h1>Content One</h1>`
		})
		new figmaPlus.Vue({
			el: modalElement2,
			template: `<h1>Content Two</h1>`
		})
	},
	null,
	null,
	null,
	null,
	null,
	['One', 'Two']
);
```

## hideUI

Hide an opened modal by providing its title.

```javascript
figmaPlus.hideUI(modalTitle);
```

- **modalTitle** (`String`): The title of the modal you want to hide.

## addTooltip

Attach a hover tooltip to a DOM element in your UI.

<img src="images/tooltip.png" width="400">

```javascript
figmaPlus.addTooltip(element, tooltipText, showAfterDelay);
```

- **element** (`DOMElement`): The DOM element to show the tooltip when hovered. E.g. an icon button.
- **tooltipText** (`String`): The text to show in the tooltip.
- **showAfterDelay (optional)** (`Boolean`): Whether to show the tooltip after a slight delay. If set to `false`, the tooltip will show immediately on hover. Default: `true`

## showToast

Show a notification message (Toast) at the bottom of the screen, with an optional action button.

<img src="images/toast.jpg" width="400">

<!-- prettier-ignore -->
```javascript
figmaPlus.showToast(
	message,
	timeoutInSeconds,
	buttonText,
	buttonAction
);
```

- **message** (`String`): Message to show in the toast.
- **timeoutInSeconds (optional)** (`Number`): Number of seconds the toast will stay on the screen. Default: `3`
- **buttonText (optional)** (`String`): The label of the action button. Must be accompanied by `buttonAction`.
- **buttonAction (optional)** (`Function`): Function to trigger when the action button is clicked. Must be accompanied by `buttonText`.

<!-- prettier-ignore -->
```javascript
// Example code for showing the toast above:
figmaPlus.showToast(
	'Something happened in your plugin!',
	3,
	'Do something',
	() => alert('You clicked the action button!')
)
```
