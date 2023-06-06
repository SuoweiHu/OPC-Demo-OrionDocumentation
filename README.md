# OPC-Demo-Docusaurus




## Potential Options
- [Webflow](https://webflow.com/?r=0)
- [GitBook](https://www.gitbook.com/)
- [Custom Project -1](https://github.com/floriannicolas/API-Documentation-HTML-Template)
- [Tailwind Protocol](https://tailwindui.com/templates/protocol)
- [FlatDoc](https://ricostacruz.com/flatdoc/#large-brief)
- [Docusaurus.io](https://docusaurus.io/)
- [ReadTheDocs](https://about.readthedocs.com/?ref=dotcom-homepage)
- [Docsify](https://docsify.js.org/#/)

## Selection Criteria
1. **No lock in contact**: not required to use any other vender services (except for source code), can host the website on varies platforms
2. **Okay community support**: not a random personal project, or proprietary custom software with little support, has to be under maintenance within 1 year
3. **Markdown support**: has to support markdown syntax (ideally MDX support)
4. **Document versioning**: has some degree of versioning support (ideally developer friendly at a code/terminal level)
5. **Searching function**: has built in global keyword search capabilities
6. **Static Site Generator**
Final pick: [Docusaurus.io](https://docusaurus.io/)

## Setup/Command Reference

**Initialize**
Running the below command will generate the scaffold for Docusaurus site building
`npx create-docusaurus@latest <site-name> <template-option> <lang-option>`
where
- `<site-name>` is the site name
- `<template-option>` is the starting point of your site and is recommended to be `classic`
- `<lang-option>` can be left empty if you are using Javascript, or `--typescript` otherwise
(e.g. `npx create-docusaurus@latest my-website classic`)

**Develop**
Running the below command will launch a local development server, serving for the purpose of previewing the changes
`npm run start / yarn run start`
By default, a browser window will open at "http://localhost:3000".

**Build**
Running the below command will build the website into a directory of static contents and put it on a web server so that it can be viewed.
`npm run build / yarn run build`
and contents will be generated within the /build directory, which can be copied to any static file hosting service like GitHub pages, Vercel or Netlify.

**Deployment**
You may use a variety of static file hosting service:
- Github Pages: https://pages.github.com/
- Vercel: https://vercel.com/
- Netlify: https://www.netlify.com/
- Amazon S3: https://aws.amazon.com/s3/

See more relating to this topic at the documentation:
- https://docusaurus.io/docs/deployment

If you are using GitHub pages for hosting, the following command is a convenient way to build the website and push to the `gh-pages` branch.
- Using SSH:`$ USE_SSH=true yarn deploy`
- Not using SSH:`$ GIT_USER=<Your GitHub username> yarn deploy`

## File Hierarchy

```
my-website
├── blog
│   ├── 2019-05-28-hola.md
│   ├── 2019-05-29-hello-world.md
│   └── 2020-05-30-welcome.md
├── docs
│   ├── doc1_file_name.md
│   ├── doc2_file_name.md
│   ├── doc3_file_name.md
│   └── mdx.md
├── src
│   ├── css
│   │   └── custom.css
│   └── pages
│       ├── styles.module.css
│       └── index.js
├── static
│   └── img
├── docusaurus.config.js
├── package.json
├── README.md
├── sidebars.js
└── yarn.lock
```

- `/blog/` - Contains the blog Markdown files. You can delete the directory if you've disabled the blog plugin, or you can change its name after setting the `path` option. More details can be found in the [blog guide](https://docusaurus.io/docs/blog)
- `/docs/` - Contains the Markdown files for the docs. Customize the order of the docs sidebar in `sidebars.js`. You can delete the directory if you've disabled the docs plugin, or you can change its name after setting the `path` option. More details can be found in the [docs guide](https://docusaurus.io/docs/docs-introduction)
- `/src/` - Non-documentation files like pages or custom React components. You don't have to strictly put your non-documentation files here, but putting them under a centralized directory makes it easier to specify in case you need to do some sort of linting/processing
	- `/src/pages` - Any JSX/TSX/MDX file within this directory will be converted into a website page. More details can be found in the [pages guide](https://docusaurus.io/docs/creating-pages)
- `/static/` - Static directory. Any contents inside here will be copied into the root of the final `build` directory
- `/docusaurus.config.js` - A config file containing the site configuration. This is the equivalent of `siteConfig.js` in Docusaurus v1
- `/package.json` - A Docusaurus website is a React app. You can install and use any npm packages you like in them
- `/sidebars.js` - Used by the documentation to specify the order of documents in the sidebar


## Docs-only-mode

mple.com/docs/temp/title", you can visit a shortened version of url "https://www.example.com/temp/title" for a "docs-only-mode" docusaurus website.

Tutorial for how to turn that on/off can be found at the following links:
- https://docusaurus.io/docs/docs-introduction
- https://www.youtube.com/watch?v=Rc6mdSRaikE

An overview of the changes are:
1. changing the configruation file to "disable blog" and "default route"
2. remove the previous root website (likely to be "/pages/index.js")
3. add corresponding root website docuemnt in the "/docs" directory, by adding `slug:/`

Changes to the configuration file is listed below
```js title="docusaurus.config.js"
>>> BEFORE
module.exports = {
  // ...
  presets: [
    '@docusaurus/preset-classic',
    {
      docs: {
        /* docs plugin options */
      },
      blog: {
        /* blog plugin options */
      },
      // ...
    },
  ],
};
<<< AFTER
module.exports = {
  // ...
  presets: [
    '@docusaurus/preset-classic',
    {
      docs: {
        routeBasePath: '/', // Serve the docs at the site's root
        /* other docs plugin options */
      },
      blog: false, // Optional: disable the blog plugin
      // ...
    },
  ],
};
===
```

