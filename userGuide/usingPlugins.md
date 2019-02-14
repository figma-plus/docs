# Using Plugins

Because Figma Plus is an open platform, it is up to the plugin developer to design the user experience and provide instructions in the **How to use** section of the detail screen. However, plugins built on our developer API typically follow a few standard patterns which make them feel more consistent to use.

## Figma Plus Menu

All plugins are recommended to have at least an item shown in the hamburger -> **Figma Plus** menu, in addition to any context menu items they might support.

<img src="images/pluginsMenu.jpg" width="400">

## Context Menus

Some plugins have actions that are contextual to specific items, these actions are usually hosted inside the item's context menu. There are many types of context menus in Figma (Click to learn more):

<details>
	<summary><b>Canvas</b></summary>
	<p>Canvas menu is suitable for global or general actions that are not specific to the selected objects.</p>

  <img src="images/canvasMenu.jpg" width="300">

</details>

<details>
	<summary><b>Selection</b></summary>

  <p>Selection menu is suitable for actions specific to the selected objects.</p>

  <img src="images/selectionMenu.jpg" width="300">

<img src="images/objectsPanelMenu.jpg" width="400">

</details>

<details>
	<summary><b>Page</b></summary>

<p>Page menu is suitable for actions specific to a page.</p>

<img src="images/pageMenu.jpg" width="400">
</details>

<details>
	<summary><b>Filename</b></summary>

<p>This is the menu that shows up when clicking on chevron next to the file name at the top. It is best used for actions specific to the current file.</p>

<img src="images/filenameMenu.jpg" width="300">
</details>

<details>
	<summary><b>Version</b></summary>

<p>Version menu is suitable for actions specific to a version in the versions pane.</p>

<img src="images/versionMenu.jpg" width="300">
</details>

<details>
	<summary><b>File</b></summary>

<p>This is the menu that shows up when right clicking on a file in the file browser. It is best used for actions specific to the selected file.</p>

<img src="images/fileMenu.jpg" width="450">
</details>

## Modals

Plugins that require more interactions can open a modal to show additional UI.

<img src="images/findAndReplace.jpg" width="400">

## Custom UI

Some plugins benefit from having custom UI integrated into the Figma interface. (We do not support this in our developer API but we don't limit this approach)

<img src="images/arabic.gif" width="500">
