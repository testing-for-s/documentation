---
title: Admin panel extension
description: Learn more about extending Strapi's admin panel.
displayed_sidebar: cmsSidebar
toc_max_heading_level: 4
tags:
  - admin panel
  - admin panel customization
---
# Admin panel extension

import HotReloading from '/docs/snippets/hot-reloading-admin-panel.md'

Strapi's [admin panel](/cms/admin-panel-customization) is a React-based single-page application that encapsulates all the features and installed plugins of a Strapi application. If the [customization options](/cms/admin-panel-customization/options) provided by Strapi are not enough for your use case, you will need to extend Strapi's admin panel.

Extending Strapi's admin panel means leveraging its React foundation to adapt and enhance the interface and features according to the specific needs of your project, which might imply creating new components or adding new types of fields.

There are 2 use cases where you might want to extend the admin panel:

- As a Strapi plugin developer, you want to develop a Strapi plugin that extends the admin panel **everytime it's installed in any Strapi application**.

  👉 This can be done by taking advantage of the [Admin Panel API for plugins](/cms/plugins-development/admin-panel-api).

- As a Strapi developer, you want to develop a unique solution for a Strapi user who only needs to extend a specific instance of a Strapi application.

  👉 This can be done by directly updating the `/src/admin/app` file, which can import any file located in `/src/admin/extensions`.

## Adding a Widget to the Sidebar

One common way to extend the admin panel is by adding a custom widget to the sidebar. This allows you to integrate additional functionality or quick-access features directly into the main navigation area of the admin panel.

To add a widget to the sidebar:

1. Create a new React component for your widget in the `/src/admin/extensions` directory.
2. In your `/src/admin/app.js` file, import your new widget component.
3. Use the `config.menu` option to add your widget to the sidebar menu. You can specify the icon, label, and any other properties required for your widget.

Here's a basic example of how you might add a custom widget to the sidebar:

```javascript
import MyCustomWidget from './extensions/MyCustomWidget';

export default {
  config: {
    locales: ['en'],
    menu: {
      customWidget: {
        icon: 'puzzle',
        label: 'My Custom Widget',
        Component: MyCustomWidget,
      },
    },
  },
  bootstrap() {},
};
```

This will add your custom widget to the sidebar with the specified icon and label. The `Component` property determines what will be rendered when the widget is clicked.

Remember to consider the overall user experience when adding new elements to the admin panel, and ensure that your custom widget provides value without cluttering the interface.

:::strapi Additional resources
* If you're searching for ways of replacing the default Rich text editor, please refer to the [corresponding page](/cms/admin-panel-customization/wysiwyg-editor).
* The  also provide extensive additional information on developing for Strapi's admin panel.
:::

