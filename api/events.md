# Events

You can use the following event listeners to trigger a function when the DOM changes.
All events are captured by a mutation observer running in the background.

## onDomChanged

Fires on any DOM changes. An array of mutation records of the change is passed as an argument in the callback function.

```javascript
figmaPlus.onDomChanged(triggerFunction(mutations));

// Example code for logging DOM changes:
figmaPlus.onDomChanged(mutations => {
	console.log(mutations);
});
```

- **triggerFunction** (`Function`): The function to trigger when the DOM changes.
- **mutations** (`Array`): An array of `MutationRecord` objects containing information on the DOM change.

## onFileBrowserLoaded

Fires when the file browser page is fully loaded. This is useful for applying styling changes to the file browser page.

```javascript
figmaPlus.onFileBrowserLoaded(triggerFunction);
```

- **triggerFunction** (`Function`): The function to trigger when the event fires.

## onFileBrowserChanged

Fires when the file browser changes from one page to another (E.g. from Recent to Drafts).

```javascript
figmaPlus.onFileBrowserChanged(triggerFunction);
```

- **triggerFunction** (`Function`): The function to trigger when the event fires.

## onFileBrowserUnloaded

Fires when the file browser page is unloaded (E.g. when opening a file).

```javascript
figmaPlus.onFileBrowserUnloaded(triggerFunction);
```

- **triggerFunction** (`Function`): The function to trigger when the event fires.

## onFileLoaded

Fires when a file is fully loaded (After the progress bar fills).

```javascript
figmaPlus.onFileLoaded(triggerFunction);
```

- **triggerFunction** (`Function`): The function to trigger when the event fires.

## onFileUnloaded

Fires when a file is unloaded (E.g. after clicking "Back to Files")

```javascript
figmaPlus.onFileUnloaded(triggerFunction);
```

- **triggerFunction** (`Function`): The function to trigger when the event fires.

## onMenuOpened

Fires when a menu is opened. Information about the opened menu are passed as arguments to the callback function.

```javascript
figmaPlus.onMenuOpened(triggerFunction(menuType, hasMoreOptions));
```

- **triggerFunction** (`Function`): The function to trigger when the event fires.
- **menuType** (`String`): A string describing the type of the opened menu (E.g. 'DROPDOWN_TYPE_CANVAS_CONTEXT_MENU').
- **hasMoreOptions** (`Boolean`): Whether the menu has more options hidden in a "More" submenu at the bottom.

## onSubmenuOpened

Fires when a sub-menu is branched off a menu. Information about the opened sub-menu are passed as arguments to the callback function.

```javascript
figmaPlus.onSubmenuOpened(triggerFunction(menuType, highlightedOption));
```

- **triggerFunction** (`Function`): The function to trigger when the event fires.
- **menuType** (`String`): A string describing the type of the opened menu (E.g. 'DROPDOWN_TYPE_CANVAS_CONTEXT_MENU').
- **highlightedOption** (`String`): The highlighted option in the main menu that the sub-menu is branched off from.

## onMenuClosed

Fires when a menu is closed.

```javascript
figmaPlus.onMenuClosed(triggerFunction;
```

- **triggerFunction** (`Function`): The function to trigger when the event fires.

## onModalOpened

Fires when a modal is opened. The title of the modal is passed as an argument into the callback function.

```javascript
figmaPlus.onModalOpened(triggerFunction(modalType));
```

- **triggerFunction** (`Function`): The function to trigger when the event fires.
- **modalType** (`String`): The title of the opened modal.

## onModalClosed

Fires when a modal is closed.

```javascript
figmaPlus.onModalClosed(triggerFunction);
```

- **triggerFunction** (`Function`): The function to trigger when the event fires.
