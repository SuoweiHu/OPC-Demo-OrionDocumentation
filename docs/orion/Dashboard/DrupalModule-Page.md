---
sidebar_position: 2
---

# Drupal Module : Page


## Workflow

### Development
If you wish to make adjustments to the React javascript, more specifically files living in  `src\Javascript\SourceCode` by running the React on a local dev web server (rather than having to compile the code, run cache clear, and hard refreshing the page every time), you can do that by doing the following:
1. copy content  `package_production.json`
2. paste it to `package.json`
3. `cd` to the level of `src\Javascript\SourceCode`
4. make adjustification to the `index.html`  and `\Component\Dashboard` in `src\Javascript\SourceCode\src`  (make some variables deterministic/hard-coded, rather than retrieving from drupal endpoints)
5. run `npm run start` to start the server
6. open browser `localhost:8080` to preview the effect of code
7. adjustification to code will automatically update the server, you don't have to run `npm` every time

### Deployment
If you wish to deploy the React javascript code to the drupal site, you will need to build it to the `src/Javascript/SourceCode/dist` by running the corresponding build command
1. copy content of `package_development.json`
2. paste it to `package.json`
3. `cd` to the level of `src\Javascript\SourceCode`
4. run `npm run build` to generate the built/minified code
5. run `(ahoy) drush cr` to clear the cache
6. !!! IMPORTANT !!!! Make sure you refresh the browser with a clear cache shortcut:
	- Command + Shift + R (Mac)
	- Ctrl + Shift + R (Win)

:::info Note

The reason for this layout of two files is for a minimum effort towards understanding usage of NPM, while also keeping a minimum usage of the dependencies for the production script.

:::



## File Hierarchies

```
\ConnectWise_Module_Page
|
|______ConnectWise_Module_Dashboard.info.yml
|
|______ConnectWise_Module_Dashboard.routing.yml
|
|______ConnectWise_Module_Dashboard.libraries.yml
|
|______\src
        |
        |_______\Controller
        |
        |_______\JavaScript
                        |_______SourceCode
                                    |_______dist
                                    |_______src
```

For the above files/directories:
- `\ConnectWise_Module_Page` :
	- Directory containing the custom module.
- `ConnectWise_Module_Dashboard.info.yml`:
	- The file of which let drupal know of this custom module, the drupal PHP will get the field "machine name", "description", "package", "compatible drupal version"  from this file.
	- [More information. ](https://www.drupal.org/docs/develop/creating-modules/let-drupal-know-about-your-module-with-an-infoyml-file)
- `ConnectWise_Module_Dashboard.routing.yml`:
	- The router of the drupal module, mapping a path like "/page/hello\_world" to some callback of controller say "/Drupal/example/ControllerExample::page\_hello\_world\_controller"; This file also defines the type of output (json/html), the permission, and library to load (e.g. javascript, CSS) for this page.
	- [ More information. ](https://www.drupal.org/docs/develop/creating-modules/create-a-custom-page-using-a-controller)
- `ConnectWise_Module_Dashboard.libraries.yml`:
	- Define library of javascript or CSS, as a reusable asset for the routers
	- [ More information. ](https://www.drupal.org/docs/develop/creating-modules/adding-assets-css-js-to-a-drupal-module-via-librariesyml)
- `\src\Controller`
	- The handler / callback for the router, it is the processing logic of the page; This file takes the parameter from router, adds a header and returns the page body.
	- [ More information. ](https://www.drupal.org/docs/develop/creating-modules/create-a-custom-page-using-a-controller)
-  `\src\Javascript\SourceCode`
	- Where the main logic of the javascript file lives, the component-wise source code (using React, Material-UI) are contained in `\src\Javascript\SourceCode\src`, and its built/compiled and minified version (using NPM RUN BUILD) are in `\src\Javascript\SourceCode\dist`
	- Notice
		- Devs: to test or develop the React source code, you can copy all the content in file `package_development.json` , paste it to `package.json` , and then running  `npm run start`.
		- Prod: to compile and build the source code, you can copy all the content in file `package_production.json` , paste it to `package.json` , and then running  `npm run build`.
		- The reason for this layout of two files is for a minimum effort towards understanding usage of NPM, while also keeping a minimum usage of the dependencies for the production script.

## Controller
There's only one controller of this module, which will return an page with an empty DOM node with specifcied ID, ready to be replaced/rendered by the React script, refer to `\src\Javascript\SourceCode\src\index.js` .