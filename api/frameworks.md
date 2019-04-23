# UI Frameworks

The `figmaPlus` API comes bundled with some UI frameworks to help you build your UI. Using these embedded frameworks is preferred over pulling in your own build, since loading only one instance of the API is more performant than multiple instances.

## React

Both [React](https://reactjs.org/docs/react-api.html) and [ReactDOM](https://reactjs.org/docs/react-dom.html) API's are available in `figmaPlus`.

To use [JSX](https://reactjs.org/docs/introducing-jsx.html), you will have to use [babel](https://reactjs.org/docs/add-react-to-a-website.html#add-jsx-to-a-project) to build your project.

```javascript
figmaPlus.React;

figmaPlus.ReactDOM;
```

<!-- prettier-ignore -->
```javascript
// Example code for rendering a button inside a modal without JSX:
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

// Example code for rendering a button inside a modal with JSX:
figmaPlus.showUI({
	title: 'React Component Demo',
	reactComponent: function Button() {
		return (
			<button onClick={() => alert('You clicked me!')}>Click me</button>
		);
	}
});
```

## Vue

[Vue](https://vuejs.org/) API is available in `figmaPlus`.

[Single file components](https://vuejs.org/v2/guide/single-file-components.html) are also supported by building the project with `vue-loader`.

```javascript
figmaPlus.Vue;
```

<!-- prettier-ignore -->
```javascript
// Example code for rendering a button inside a modal:
figmaPlus.showUI({
	title: 'Vue Component Demo',
	vueComponent: figmaPlus.Vue.component('demo-button', {
		template: `<button @click="alert('You clicked me!')">Click me</button>`
	})
});
```
