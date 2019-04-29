# Using Plugins

Because Figma Plus is an open platform, it is up to the plugin developer to design the user experience and provide instructions in the **How to use** section of the detail screen. However, plugins built on our developer API typically follow a few standard patterns which make them feel more consistent to use.

## Figma Plus Menu

All plugins are recommended to have at least an item shown in the hamburger -> **Figma Plus** menu, in addition to any context menu items they might support.

<img src="images/pluginsMenu.png" width="400">

!> Some plugin actions only show when the right conditions are met. For example, an action that applies to selected items will only show when you have selected at least one item in the canvas.

## Canvas Menu

Right clicking on the canvas area opens the Canvas Menu. Plugins can optionally be added to this menu as a shortcut if they are frequently used.

<img src="images/canvasMenu.png" width="250">

## Selection Menu

Right clicking on selected objects in the canvas or the layers pane opens the Selection Menu. Plugins can use this menu to add contextual commands that apply to the selection.

<img src="images/selectionMenu.png" width="600">

## Modals

Plugins that require more interactions can open a modal to show additional UI.

<img src="images/findAndReplace.png" width="350">

## Custom UI

Some plugins benefit from having custom UI integrated into the Figma interface.

<img src="images/arabic.gif" width="500">
