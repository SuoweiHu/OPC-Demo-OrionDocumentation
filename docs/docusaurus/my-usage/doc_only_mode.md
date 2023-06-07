---

sidebar_order: 4
title: "Docs-only-mode"
---


### Docs-only-mode

This site has turned on "docs-only-mode" which means any of the documentation under the sub-directory will be displayed at the root, for instance you have document "docs/temp/readme.md", then instead of visiting "https://www.example.com/docs/temp/title", you can visit a shortened version of url "https://www.example.com/temp/title" for a "docs-only-mode" docusaurus website.

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

