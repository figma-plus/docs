# Figma Plus API

The Figma Plus API is available as a global variable `window.figmaPlus` (or simply `figmaPlus`) on every page after Figma Plus is installed.

Here are some examples of what you can do with the API. You can copy and run the code in the console to test them out.

### Add a command to the Figma Plus menu

```javascript
figmaPlus.addCommand({
	label: 'My Awesome Plugin',
	action: () => alert('Plugin is running!')
});
```

### Attach a keyboard shortcut to an action

```javascript
figmaPlus.registerKeyboardShortcut({
	shortcut: {
		mac: { command: true, key: 'P' },
		windows: { control: true, key: 'P' }
	},
	action: () => alert('Plugin is running!')
});
```

### Show a toast message

```javascript
figmaPlus.showToast({ message: 'Plugin is running!' });
```

### Show a modal

```javascript
figmaPlus.showUI({
	title: 'HTML Demo',
	html: `<button>Click me</button>`,
	onMount: modalContent => {
		modalContent.firstChild.onclick = () => alert('You clicked me!');
	}
});
```

### Get properties of the selected object

```javascript
figmaPlus.currentPage.selection[0].getProperties().then(node => console.log(node));
```

### Update properties of the selected object

```javascript
figmaPlus.currentPage.selection[0].getProperties().then(node => (node.width = 100));
```

## Get a list of local and library styles

```javascript
figmaPlus.styles;
```

## Show node ID's in the layers panel

```javascript
figmaPlus.toggleShowNodeId();
```
