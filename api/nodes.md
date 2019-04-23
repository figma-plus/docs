# Nodes

Nodes are elements in your current Figma document, such as pages, frames and layers. You can get node objects by their ID using the `figmaPlus.getNodeById` function, or by browsing through your document's node tree using `figmaPlus.root`.

## Node object

The Node object contains information about your node, such as its ID, name and type.

You can learn more about node types from [Figma's API documentation](https://www.figma.com/developers/docs#node-types).

#### Global properties

Global properties exist on every `node`. All global properties are **read-only** unless otherwise specified.

Please refer to [Figma's API documentation](https://www.figma.com/developers/docs#global-properties) for more information on global properties.

```
id: <String>			// Unique ID of the node
type: <String>			// Type of node, e.g. 'FRAME', 'TEXT', etc.
parent: <Node>			// Returns the parent node
children: <Array>		// Array of children nodes, if it has any
name: <String>			// Editable using node.name = 'newName'
visible: <Boolean>		// Editable using node.visible = <Boolean>
locked: <Boolean>		// Editable using node.locked = <Boolean>
absoluteBounds: {		// Absolute position and size of the node on the canvas
	x: <Number>,
	y: <Number>,
	width: <Number>,
	height: <Number>
}
relativeTransform: <Array>	// Relative position and rotation to the parent
characters: <String>		// Text content of a text node. Editable using node.characters = 'New Text'

```

#### Properties

To get display properties like fill colors and font size, you will need to call `node.getProperties()` which returns a promise with the node object with properties. (Referred to as `newNode` below)

Non-global properties are all editable simply by setting a new value in the callback function. E.g. `newNode.fontSize = 14`

<!-- prettier-ignore -->
```javascript
// Example code for setting a text node's font size to 14:
node.getProperties().then((newNode) => {
	newNode.fontSize = 14;
});

// Example code for setting an array of text node's font size to 14:
async function setFontSizes() {
	for(node of arrayOfTextNodes) {
    const newNode = await node.getProperties();
		newNode.fontSize = 14;
	}
}

setFontSizes();
```

Please refer to [Figma's API documentation](https://www.figma.com/developers/docs#node-types) for more information on node properties.

### getAllDescendents

Run this function on a node to get an array of all descendents (children, grandchildren, etc.) of a node with children. This is useful for iterating over all nodes inside a subtree without recursion.

```javascript
node.getAllDescendents();
```

### export

Run this function on a node to render it as an image. This returns a Promise of an object with `blob`, `buffer` and `url` which is the output of the image in different formats.

```javascript
node.export(options);
```

- **options (optional)** (`Object`): An object used to set the `format` and `contentsOnly` parameter. Currently only PNG format is supported. Default: `{ format: "PNG", contentsOnly: true }`

```javascript
// Render a contents-only image of a node in PNG format :
node.export();

// Render a non-contents-only image of a node in PNG format :
node.export({ format: 'PNG', contentsOnly: false });

// Example code for showing an image of the selected node in a modal:
async function displayNodeAsImage() {
	const node = figmaPlus.currentPage.selection[0];
	const url = await node.export().then(image => image.url);
	const image = await new Promise((resolve, reject) => {
		const i = new Image();
		i.onload = () => resolve(i);
		i.onerror = () => reject();
		i.src = url;
	});
	figmaPlus.showUI({
		title: node.name,
		onMount: modalContent => {
			modalContent.appendChild(image);
		},
		width: image.width,
		height: image.height
	});
}

displayNodeAsImage();
```

---

# Functions to get Nodes

## getNodeById

Look up a node by its ID string.

```javascript
figmaPlus.getNodeById(nodeId);
```

- **nodeId** (`String`): A node's ID number, e.g. "1:23"

## root

Get the document node. Each child is a page.

```javascript
figmaPlus.root;
```

## currentPage

Get the current page node. Everything on the current page can be found under this node.

```javascript
figmaPlus.currentPage;
```

## selection

Get an array of all selected nodes.
You can also set your selection by passing an array of node objects or node ID's.

```javascript
// Get selection
figmaPlus.currentPage.selection;

// Set selection by an array of node objects
figmaPlus.currentPage.selection = [node];

// Set selection by an array of node ID's
figmaPlus.currentPage.selection = [nodeId];
```

- **node** (`Node`): See [Node object](#node-object) above.
- **nodeId** (`String`): A node's ID number, e.g. "1:23"

## centerOnPoint

Set the viewport translation and scale values.

```javascript
figmaPlus.scene.centerOnPoint(
	point: {x, y},
	zoomScale
);
```

- **x** (`Number`): Absolute vertical position on the canvas.
- **y** (`Number`): Absolute horizontal position on the canvas.
- **zoomScale (optional)** (`Number`): The zoom level of the viewport. Default: `1`

## panToNode

Center the viewport to the provided node (Without zooming).

```javascript
// Pan to a node by its node object
figmaPlus.scene.panToNode(node);

// Pan to a node by its node ID
figmaPlus.scene.panToNode(nodeId);
```

- **node** (`Node`): See [Node object](#node-object) above.
- **nodeId** (`String`): A node's ID number, e.g. "1:23"

## zoomOnNodes

Zoom the viewport to contain the provide nodes.

```javascript
// Pan to a node by an array of node objects
figmaPlus.scene.zoomOnNodes([node]);

// Pan to a node by an array of node ID's
figmaPlus.scene.zoomOnNodes([nodeId]);
```

- **node** (`Node`): See [Node object](#node-object) above.
- **nodeId** (`String`): A node's ID number, e.g. "1:23"
