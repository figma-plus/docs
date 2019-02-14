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
figmaPlus.showUI(
	'Hello world',
	(modalElement) => {
		const button = figmaPlus.React.createElement(
			"button",
			{ class: "button primary"},
			"Button"
		);
		figmaPlus.ReactDOM.render(button, modalElement);
	}
);

// Example code for rendering a button inside a modal with JSX:
figmaPlus.showUI(
	'Hello world',
	(modalElement) => {
		const button = <button class="button primary">Button</button>;
		figmaPlus.ReactDOM.render(button, modalElement);
	}
);
```

## Vue

[Vue](https://vuejs.org/) API is available in `figmaPlus`.

[Single file components](https://vuejs.org/v2/guide/single-file-components.html) are also supported by building the project with `vue-loader`.

```javascript
figmaPlus.Vue;
```

<!-- prettier-ignore -->
```javascript
// Example code for rendering a button inside a modal using template literals:
figmaPlus.showUI(
	'Hello world',
	(modalElement) => {
		new figmaPlus.Vue({
			el: modalElement,
			template: `<button class="button primary">Button</button>`
		})
	}
);

// Example code for rendering a component inside a modal:
figmaPlus.showUI(
	'Hello world',
	(modalElement) => {
		new figmaPlus.Vue({
			el: modalElement,
			render: h => h(component)
		})
	}
);
```
