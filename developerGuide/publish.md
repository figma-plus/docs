# Publishing a Plugin

When you are done building your plugin and would like to share it to the Figma Plus community, follow this guide to publish your plugin.

?> To ensure all published plugins are open-sourced and available for review, they must be hosted on public Github repos.

## Manifest file

Each publishable plugin must have a `manifest.json` file in the root folder to descibes how the plugin is presented to users.

Here's an example:

```javascript
{
	"id": "find-and-replace",
	"name": "Find and Replace",
	"author": "Jackie Chui",
	"description": "Find and replace texts and layer names in your Figma document.",
	"instructions": "Right click on the canvas and select 'Find and Replace', or by pressing Control/Command + F.",
	"images": [
		"https://raw.githubusercontent.com/jachui/figma-find-and-replace-desktop/gh-pages/screenshots/animation.gif",
		"https://raw.githubusercontent.com/jachui/figma-find-and-replace-desktop/gh-pages/screenshots/screenshot1.jpg",
		"https://raw.githubusercontent.com/jachui/figma-find-and-replace-desktop/gh-pages/screenshots/screenshot2.png"
	],
	"js": [
		"dist/js/chunk-vendors.js",
		"dist/js/app.js"
	],
	"css": [
		"dist/css/app.css"
	]
}
```

<details><summary>Show desciptions of keys</summary>
<p>

- **id**: Unique ID of your plugin.
- **name**: Display name of your plugin to users.
- **author**: Your name.
- **description**: Short description of what your plugin does.
- **instructions**: Insturctions on how to use your plugin.
- **images**: Array of URL's to your plugin's screenshot. URL's can either be full addresses or relative path from the Github project's root (E.g. `screenshot/preview.png`).
- **js**: Array of paths to your js files relative to your Github project's root.
- **css**: Array of paths to your css files relative to your Github project's root.
- **requiredOrgId (optional)** (`String`): ID of the Org that you want the plugin to only show in. Users outside of this Org will not see this plugin. You can get your current Org's ID from `figmaPlus.myOrg`.
- **requiredTeamIds (optional)** (`Array of Strings`): Array of the teams that you want the plugin to only show in. Users outside of these teams will not see this plugin. You can get your teams' IDs from `figmaPlus.myTeams`.

</p>
</details>

## Create Github Release

To publish your plugin, head over to your project's Github repo and create a new release of the current version. Learn more about [Github Releases](https://help.github.com/articles/creating-releases/).

<img src="images/githubRelease.jpg" width="600">

Tag your release with a version number, ideally in the following format:

`1.0.0` (No need to add the prefix `v`)

You can name your release anything you want (or leave it blank), we don't track it in the plugin manager.

Add descriptions of your current release, this will show up in the update log in your plugin's detail page. If this is your first release of the plugin, enter `Initial release`.

## Request for Approval

To protect Figma Plus users from any malicious code. We must review your plugin's code to check for any security threats. Here are some things we look for when approving a plugin release:

- Does the plugin work
- Security threats such as sending user data to a server, including analytics scripts
- Damages to users' documents

To submit a request for approval, add a new entry in our [Plugin Directory](https://github.com/figma-plus/plugin-directory/blob/gh-pages/plugins.json) and create a pull request.

A plugin entry looks like this:

```javascript
{
	"id": "my-awesome-plugin",
	"github": "https://github.com/user/my-awesome-plugin",
	"approvedVersion": "1.0.0",
	"approvedCommit": "f0155878d5412ba439aa2bfa44eea5295dd9cf16"
}
```

- **id**: Unique ID of your plugin.
- **github**: URL to your plugin's Github project.
- **approvedVersion**: The tag (e.g. `1.0.0`) of your latest Github release.
- **approvedCommit**: The commit hash of your latest Github release.

<details><summary>Click to see how to get your commit hash of your Github release</summary>
<p>

Click on the hash button below your release tag.

<img src="images/commitHash1.png" width="500">

Find the string of commit hash here:

<img src="images/commitHash2.png" width="700">

</p>
</details>

Upon reviewing the plugin's code, we will merge the pull request so Figma Plus users can find and install your plugin in the plugin manager.

## Updating a Plugin

Updating a published plugin is a similar process to publishing a new plugin.

Create a new release on Github with a new version tag (e.g. `1.0.1`), include some notes about your update in the descriptions.

Then update your plugin's entry in the [Plugin Directory](https://github.com/figma-plus/plugin-directory/blob/gh-pages/plugins.json) with a new `approvedVersion` and `approvedCommit` then create a pull request.

```javascript
{
	"id": "my-awesome-plugin",
	"github": "https://github.com/user/my-awesome-plugin",
	"approvedVersion": "1.0.1",
	"approvedCommit": "eaf05840f13b4f673354ddadc9d672659b579835"
}
```

Upon reviewing the new version's code, we will merge the pull request so Figma Plus users can automatically receive the updates.
