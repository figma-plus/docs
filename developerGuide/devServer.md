# Development Server

Using a development server allows you to develop with local files, use your favorite code editor and build complex plugins that require a build process.

## Setup

> If you are already familiar with setting up development servers with webpack or other build tools, you can skip this section and move on to connecting your server to Figma Plus.

?> Prerequisite: You will need [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/) installed on your machine.

The simplest way to set up a development server is to use `http-server`. We recommend installing it globally:

```
npm install http-server -g
```

To create a server on a folder containing your plugin's Javascript files, enter the following:

```
http-server [path to folder] --cors
```

If you are using a build tool, you should point to the build destination (e.g. `/dist`) instead of the project root.

## Connect to Figma Plus

?> Please make sure your development server has [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) enabled, this is required for Figma to request content from your server. If you are using `http-server`, make sure `--cors` is included after the folder's path.

Select the **Developer** tab from the plugin manager, and enter information about your server and files.

<img src="images/devServer.png" width="450">

- **Port**: Port Number of your development server. Most servers default to `8080`.
- **Javascript Files**: Add the paths to your `.js` files on your server. Note that the files are loaded in the displayed order, make sure to enter the paths in the order the files should load in.
- **CSS Files**: Add the paths to your `.css` files if there are any.

When you are done, click **Connect** and refresh your page to run your plugin.
