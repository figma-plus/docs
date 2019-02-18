# Figma Plus API

To make plugin development easier, we have created an API that allows you to communicate with the opened Figma document and the UI around it.

The Figma Plus API is available as a global variable `window.figmaPlus` (or simply `figmaPlus`) on every page after Figma Plus is installed.

Here are some examples of what you can do with the API. You can copy and run them in the console to test it out.

### Add an action item to the Figma Plus menu

```javascript
figmaPlus.createPluginsMenuItem('My Awesome Plugin', () => alert('Plugin is running!'));
```

### Attach a keyboard shortcut to an action

```javascript
figmaPlus.createKeyboardShortcut(
	{
		mac: { command: true, key: 'P' },
		windows: { control: true, key: 'P' }
	},
	() => alert('Plugin is running!')
);
```

### Show a toast message

```javascript
figmaPlus.showToast('Plugin is running!');
```

### Show a modal

```javascript
figmaPlus.showUI('My Awesome Plugin', modalElement => {
	figmaPlus.ReactDOM.render('Plugin is running!', modalElement);
});
```

### Get properties of the selected object

```javascript
figmaPlus.scene.selection[0].getProperties().then(node => console.log(node));
```

### Update properties of the selected object

```javascript
figmaPlus.scene.selection[0].getProperties().then(node => (node.width = 100));
```

## Show node ID's in the layers panel

```javascript
figmaPlus.toggleShowNodeId();
```
