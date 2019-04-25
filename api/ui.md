# UI Functions

Use these functions to set up your plugin and insert menu items for users to interact with.

## addCommand

Create a command in the **Figma Plus** menu.

<img src="images/pluginsMenu.png" width="400">

<!-- prettier-ignore -->
```javascript
figmaPlus.addCommand({
	label,
	action,
	shortcut,
	condition,
	submenu,
	showInCanvasMenu,
	showInSelectionMenu,
	hideInMainMenu
});
```

- **label** (`String`): The label of the command.
- **action** (`Function`): Action to trigger when the command is clicked. If there are sub-menus, this action will not be runned on click.
- **shortcut (optional)** (`Shortcut`): An object defining the keyboard shortcut for both Mac and Windows.

```
// Shortcut object format
{
	mac: {
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

- **condition (optional)** (`Function`): Condition function that determines whether the command is shown in the menu. Commands will only show when the condition function returns `true`.

* **submenu (optional)** (`Array`): An array of `Command` objects to show a sub-menu with more commands.

```
// Command object format
{
	label: <String>,
	action: <Function>,
	shortcut: <Shortcut> (optional),
	condition: <Function> (optional)
}
```

- **showInCanvasMenu (optional)** (`Boolean`): Show command in the canvas right click menu. Default: `false`
  <img src="images/canvasMenu.png" width="250">

- **showInSelectionMenu (optional)** (`Boolean`): Show command in the selection right click menu. Default: `false`
  <img src="images/selectionMenu.png" width="600">
- **hideInMainMenu (optional)** (`Boolean`): Hide the command in the Figma Plus plugins menu. Use this in combination with `showInCanvasMenu` or `showInSelectionMenu` to create commands that only show in the canvas or selection right click menus. Default: `false`

<!-- prettier-ignore -->
```javascript
// Example code for creating a simple plugin command:
figmaPlus.addCommand({
	label: 'Hello world!',
	action: () => alert('Hello world!')
});

// Example code for creating a plugin command with a keyboard shortcut:
figmaPlus.addCommand({
	label: 'Hello world!',
	action: () => alert('Hello world!'),
	shortcut: {
		mac: {
			shift: true,
			command: true,
			key: 'O'
		},
		windows: {
			control: true,
			shift: true,
			key: 'O'
		}
	}
});

// Example code for creating a plugin command with a sub-menu:
figmaPlus.addCommand({
	label: 'Hello world!',
	action: () => alert('Hello world!'),
	submenu: [
		{
			label: 'Hello',
			action: () => alert('Hello')
		},
		{
			label: 'World',
			action: () => alert('World')
		}
	]
});
```

## registerKeyboardShortcut

Attach an action function to a keyboard shortcut. This is only useful if the action you want to trigger is not in the command menu, otherwise passing a `Shortcut` object to `figmaPlus.addCommand` is a better way to add keyboard shortcuts to your actions.

<!-- prettier-ignore -->
```javascript
figmaPlus.registerKeyboardShortcut({
	shortcut,
	action,
	condition
});
```

- **shortcut** (`Shortcut`): An object defining the keyboard shortcut for both Mac and Windows.

```
// Shortcut object format
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

- **action** (`Function`): Action to trigger when the keyboard shortcut is pressed.
- **condition (optional)** (`Function`): Condition function that determines whether the keyboard shortcut will trigger the action. Actions will only run when the condition function returns `true` at the time the shortcut is pressed.

```javascript
// Example code for creating a simple keyboard shortcut:
figmaPlus.registerKeyboardShortcut({
	shortcut: {
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
	action: () => alert('Hello world!')
});
```

## showUI

Show a Figma styled modal where you can attach a UI onto, using either HTML, a React component or a Vue components.

<img src="images/modal.png" width="400">

```javascript
figmaPlus.showUI({
	title,
	html,
	reactComponent,
	vueComponent,
	onMount,
	width,
	height,
	positionX,
	positionY,
	overlay,
	padding,
	useFigmaStyles,
	tabs
});

// Use only one of html, reactComponent or vueComponent.
```

- **title** (`String`): The title to show on the modal header.
- **html (optional)** (`String`): HTML to render inside the modal. Use the `onMount` function to run scripts after the HTML is rendered.
- **reactComponent (optional)** (`React Component`): Pass in a React component to render inside the modal.
- **vueComponent (optional)** (`Vue Component`): Pass in a Vue component to render inside the modal.
- **onMount (optional)** (`Function`): Function to run after the UI is loaded. The mounted element is passed into the function. Use this to interact with the elements created in your `html` string.
- **width (optional)** (`Number`): Width of the modal in px. Default: `300`
- **height (optional)** (`Number || String`): Height of the modal in px or 'auto' (Height of the inner elements). Default: `"auto"`
- **positionX (optional)** (`Number`): Horizontal position in % relative to the screen, ranges from 0 to 1. Default: `0.5` (Center of the screen)
- **positionY (optional)** (`Number`): Vertical position in % relative to the screen, ranges from 0 to 1. Default: `0.5` (Center of the screen)
- **overlay (optional)** (`Boolean`): Whether the modal has a dark overlay background. Default: `false`
- **padding (optional)** (`Boolean`): Whether to include the default padding (`padding: 16px 8px`) around the modal content. Default: `true`
- **useFigmaStyles (optional)** (`Boolean`): Set this to `false` to remove all Figma control styling in the content area. Default: `true`
- **tabs (optional)** (`Array`): Pass in an array of `Tab` objects to render a modal with tabbed content. Note that if you use `tabs`, the `html`, `reactComponent`, `vueComponent` and `onMount` properties **outside** of the `tabs` array will be ignored.

```
// Tab object format
{
	title: <String>,
	html: <String> (optional),
	reactComponent: <React Component> (optional),
	vueComponent: <Vue Component> (optional),
	onMount: <Function> (optional)
}
```

<img src="images/tabbedModal.png" width="400">

<!-- prettier-ignore -->
```javascript
// Attaching UI using pure HTML/Javascript
figmaPlus.showUI({
	title: 'HTML Demo',
	html: `<button>Click me</button>`,
	onMount: modalContent => {
		modalContent.firstChild.onclick = () => alert('You clicked me!');
	}
});

// Attaching UI using a React component
// React and ReactDOM are available in figmaPlus.React and figmaPlus.ReactDOM)
// You can also use JSX if babel is installed

figmaPlus.showUI({
	title: 'React Component Demo',
	reactComponent: function Button() {
		return (figmaPlus.React.createElement(
			"button",
			{ onClick: () => alert('You clicked me!') },
			"Click me")
		);
	}
});

// Attaching UI using a Vue component
// Vue is available in figmaPlus.Vue
figmaPlus.showUI({
	title: 'Vue Component Demo',
	vueComponent: figmaPlus.Vue.component('demo-button', {
		template: `<button @click="alert('You clicked me!')">Click me</button>`
	})
});

// Attaching UI to multiple tabs
figmaPlus.showUI({
	title: 'Tab Demo',
	tabs: [
		{title: 'Tab 1', html: `<h1>This is Tab 1</h1>`},
		{title: 'Tab 2', html: `<h1>This is Tab 2</h1>`}
	]
});
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
figmaPlus.addTooltip({
	element,
	text,
	showAfterDelay
});
```

- **element** (`DOMElement`): The DOM element to show the tooltip on when hovered. E.g. an icon button.
- **text** (`String`): The text to show in the tooltip.
- **showAfterDelay (optional)** (`Boolean`): Whether to show the tooltip after a slight delay. If set to `false`, the tooltip will show immediately on hover. Default: `true`

## showToast

Show a notification message (Toast) at the bottom of the screen, with an optional action button.

<img src="images/toast.png" width="400">

<!-- prettier-ignore -->
```javascript
figmaPlus.showToast({
	message,
	timeoutInSeconds,
	buttonText,
	buttonAction
});
```

- **message** (`String`): Message to show in the toast.
- **timeoutInSeconds (optional)** (`Number`): Number of seconds the toast will stay on the screen. Default: `3`
- **buttonText (optional)** (`String`): The label of the action button. Must be accompanied by `buttonAction`.
- **buttonAction (optional)** (`Function`): Function to trigger when the action button is clicked. Must be accompanied by `buttonText`.

<!-- prettier-ignore -->
```javascript
// Example code for showing the toast above:
figmaPlus.showToast({
	message: 'Something happened in your plugin!',
	buttonText: 'Do something',
	buttonAction: () => alert('You clicked the action button!')
});
```
