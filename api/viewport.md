# Viewport

The `figmaPlus.viewport` object allows you to get and set the position and zoom level of your canvas.

## center

Get and set the position of the canvas.

```javascript
// Get canvas position
figmaPlus.viewport.center;

// Set canvas position
figmaPlus.viewport.center = { x, y };
```

- **x** (`Number`): X position of the canvas.
- **y** (`Number`): Y position of the canvas.

## zoom

Get and set the zoom level of the canvas.

```javascript
// Get canvas position
figmaPlus.viewport.zoom;

// Set canvas position
figmaPlus.viewport.zoom = zoomScale;
```

- **zoomScale** (`Number`): Zoom level of the canvas.

## scrollAndZoomIntoView

Zoom the canvas to an array of nodes.

```javascript
// Zoom in by an array of node object
figmaPlus.scrollAndZoomIntoView([node]);

// Zoom in by an array of node ID's
figmaPlus.scrollAndZoomIntoView([nodeId]);
```

- **node** (`Node`): See [Node object](api/nodes#node-object).
- **nodeId** (`String`): A node's ID number, e.g. "1:23"

## panToNode

Pan the canvas to a node while keeping the current zoom level.

```javascript
// Pan to a node by its node object
figmaPlus.zoomToNode(node);

// Pan to a node by its node ID's
figmaPlus.zoomToNode(nodeId);
```

- **node** (`Node`): See [Node object](api/nodes#node-object).
- **nodeId** (`String`): A node's ID number, e.g. "1:23"
