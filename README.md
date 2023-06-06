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

## Setup

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

