# Styles

You can get a list of local and library styles using the `figmaPlus.styles` API.

## Style object

The Style object contains information about your style, such as its ID, name and type.

You can learn more about style properties from [Figma's API documentation](https://www.figma.com/developers/docs#library-items-types).

```
id: <String>			// Unique ID of the style. Can be used to apply style to a node (See example below)
type: <String>		// Type of style, e.g. 'FILL', 'TEXT', 'EFFECT'
name: <String>
description: <String>
remote: <Boolean>			// Whether this style is in a library (non-local)
thumbnail_url: <String>		// This can be used to render a thumbnail of the style
canvas_url: <String>		// This is the URL of where the style's data is stored
fills/effects/layoutGrids: <Array> // Array of properties of the style
```

```javascript
// Apply a style to a node using its style ID:
node.getProperties().then(node => {
	node.fillStyleId = style.id;
});
```

### local

Get an array of all local styles in your document.

```javascript
figmaPlus.styles.local;
```

### libraries

Get all shared styles organized by libraries.

```javascript
figmaPlus.styles.libraries;
```

```
// Library object

name: <String>		// Name of the library
key: <String>			// File key of the library
styles: <Array>		// Array of styles in the library
```

### addedLibraries

Get all shared styles from only libraries you have added in the document.

```javascript
figmaPlus.styles.addedLibraries;
```

### findAll

Find all styles that the `callback` function returns true. If `callback` is not provided, this will returns all styles (both local and published).

```javascript
figmaPlus.styles.findAll(callback);
```

- **callback (optional)** (`Function`): Function to test each style against.

```javascript
// Return all styles:
figmaPlus.styles.findAll();

// Return all effect styles:
figmaPlus.styles.findAll(style => style.type === 'EFFECT');
```

### findOne

Find the first style the `callback` function returns true. If no results are found, it will return `null`.

```javascript
figmaPlus.styles.findOne(callback);
```

- **callback** (`Function`): Function to test each style against.

```javascript
// Find the first descendent of a node named 'Primary Color'
figmaPlus.styles.findOne(style => style.name === 'Primary Color');
```

## getStyleById

Get a style by its ID.

```javascript
figmaPlus.getStyleById(styleId);
```
