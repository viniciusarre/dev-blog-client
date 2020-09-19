---
id: 3
title: "Build a blog using Markdown files with Gridsome and Vuetify"
strapline: "In this post, we will build a Blog using Gridsome, MarkDown files and Vuetify"
date: 2020-09-14
author: "Vinícius Arré"
slug: "build-a-gridsome-blog"
---

## Introduction
<br/>
If you haven't yet heard of [Gridsome](https://gridsome.org/) , it's a Vue.js-based Jamstack frame work which generates blazing fast static-sites. It is very useful for consuming RESTFul or GraphQL requests and statically show them. It also is a great way to be a headless CMS, for several other clients. 
<br><br>

## Part 1: Installing and setup
<br>
Note: if you'd like to skip this part, you can find a template which already sets up the Markdown file configuration as well as Vuetify with Gridsome [here](https://github.com/viniciusarre/gridsome-blog-template).
<br>
If you are using NPM, simply run:

`npm install -g @gridsome/cli`

Then, we need create a new project, let's call this blog `markdown-blog`. To do so, simply run:

`gridsome create markdown-blog`

Then, after its creation, we'll proceed to our own custom configuration...

## Installing the dependencies

We will need to install and configure the plugin for handling the Markdown files (we'll use transformer remarks for such), as well as another one to help us deal with a source file-system. They're both provided as gridsome plugins by the community...

You can install them by running:

` npm install --save @gridsome/source-filesystem @gridsome/transformer-remark`

Then, you will need to install Vuetify and the MDI fonts... you can do so by running:

`npm install --save vuetify @mdi/font`

Furthermore, a few development-only dependencies will be needed in order to transpile Vuetify:

`npm install --save-dev sass-loader sass vuetify-loader webpack-node-externals`

<br>

## Configuring Vuetify

In order to configure Vuetify, you need to edit the ´gridsome.server.js´ file and assure that you import and properly reference Vuetify so that it gets properly transpiled into the final static gridsome page. Make it looks something like this:

```
const nodeExternals = require('webpack-node-externals')
const VuetifyLoaderPlugin = require('vuetify-loader/lib/plugin');

module.exports = function (api) {
  api.chainWebpack((config, { isServer }) => {
    if (isServer) {
      config.externals([
        nodeExternals({
          allowlist: [/^vuetify/]
        })
      ])
    }
  })

  api.chainWebpack((config, { isServer }) => {
    config.plugin('vuetify-loader').use(VuetifyLoaderPlugin);
  });
}
```

At last, import Vuetify and its dependencies on `main.js`. By default, there's the import for the Layout file. We can add Vuetify by doing this:

1. Import Vuetify
   `import Vuetify from "vuetify"`
2. Then, add the initialization of it as well as its styling reference to the function. It must look like something similar to this:

```
// This is the main.js file. Import global CSS and scripts here.
// The Client API can be used here. Learn more: gridsome.org/docs/client-api

import Vuetify from "vuetify";

import DefaultLayout from "~/layouts/Default.vue";

export default function(Vue, { router, appOptions, head, isClient }) {
  head.link.push({
    rel: 'stylesheet',
    href: 'https://cdn.jsdelivr.net/npm/@mdi/font@latest/css/materialdesignicons.min.css',
  })
  
  head.link.push({
    rel: 'stylesheet',
    href: 'https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;500;700;900',
  });


  const opts = {
    icons: {
      iconfont: "mdi",
    },
    theme: {
      dark: true,
      themes: {
        dark: {
          primary: '#8BC34A',
          accent: '#455A64',
          secondary: '#757575',
          info: '#FFFFFF',
          success: '#8BC34A'
        }
      }
    }
  }; // opts includes, vuetify themes, icons, etc.
  Vue.use(Vuetify);
  appOptions.vuetify = new Vuetify(opts);

  // Set default layout as a global component
  Vue.component("Layout", DefaultLayout);
}
```

``
<br>

## Configuring the plugins

You will need to edit the file ´gridsome.config.js` in order to use the plugins we installed, as well as passing options and other parameters to them. Make sure to push this to your ´plugins´ Array:

```
  plugins: [
    {
      use: '@gridsome/source-filesystem',
      options: {
        path: 'content/**/*.md',
        typeName: 'BlogPost',
        route: '/content/:slug',
        remark: {
          // pass other remark options here, if needed
        }
      }
    }
  ],
```
This configures the folder and type of file which will be used and then add a typeName to handle this type of data (more on this later). As you can see, the route will look for content on a given slug, therefore, when creating the posts, we will be redirected to the given slug so that that post can be rendered.


## Part 2: Implementing a layout and writing the first Blog Post file
<br>

## Implementing a Layout 

We will create a two column design for the blog. You can see the design file by navigating to `src/Layouts/Default.vue`. You can add this in order to get started, but feel free to get more creative!

```





```




 