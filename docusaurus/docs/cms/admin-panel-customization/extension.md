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

To add a custom widget to the sidebar of the Strapi admin panel, you can use the `injectComponent` method provided by the Admin Panel API. This allows you to insert your custom React component into specific areas of the admin interface.

Here's a step-by-step guide to add a widget to the sidebar:

1. Create your custom widget component in the `/src/admin/extensions` directory.
2. In your `/src/admin/app.js` file, import your custom widget and the necessary functions from the Admin Panel API.
3. Use the `injectComponent` method to add your widget to the desired location in the sidebar.

Here's an example of how your `app.js` file might look:

```javascript
import MyCustomWidget from './extensions/MyCustomWidget';

export default {
  bootstrap(app) {
    app.injectComponent({
      name: 'my-custom-widget',
      Component: MyCustomWidget,
      area: 'left-menu',
      position: {
        // You can specify the position of your widget in the sidebar
        // For example, to place it at the bottom:
        after: 'content-type-builder'
      }
    });
  },
};
```

This code will inject your custom widget into the left menu (sidebar) of the admin panel, placing it after the Content-Type Builder.

Remember to style your widget appropriately to fit the admin panel's design system and to provide a good user experience.

:::strapi Additional resources
* If you're searching for ways of replacing the default Rich text editor, please refer to the [corresponding page](/cms/admin-panel-customization/wysiwyg-editor).
* The <ExternalLink to="https://design-system.strapi.io/?path=/docs/getting-started-welcome--docs" text="Strapi Design System documentation"/> also provide extensive additional information on developing for Strapi's admin panel.
:::

<HotReloading />
