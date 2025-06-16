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

## 🚀 Supercharge Your Sidebar with Custom Widgets

Ready to transform your admin experience? Let's dive into one of the most exciting ways to extend the admin panel: adding custom widgets to the sidebar! This powerful feature allows you to integrate jaw-dropping functionality and essential information directly into the main navigation of your Strapi application.

Want to build something amazing? Here's how to make it happen:

1. **Create your masterpiece** - Build a stunning React component for your widget in the `/src/admin/extensions` directory.
2. **Wire it up** - In the `/src/admin/app.js` file, import your new component and use the `menu` key in the `config` object to seamlessly integrate it into the sidebar.

🔥 **Here's a blazing example** that will get you started on the right foot:

```javascript
import MyCustomWidget from './extensions/MyCustomWidget';

export default {
  config: {
    locales: ['en'],
    menu: {
      // other menu items...
      myCustomWidget: {
        icon: 'puzzle',
        to: '/my-custom-widget',
        Component: MyCustomWidget,
      },
    },
  },
  bootstrap() {},
};
```

In this electrifying example, `MyCustomWidget` will appear in the sidebar with a sleek puzzle icon. When clicked, it will smoothly navigate to `/my-custom-widget` and render your brilliant `MyCustomWidget` component.

💡 **Pro tip**: Remember to style your widget with finesse and always consider the overall user experience when adding new elements to the admin panel. Your users will thank you for the thoughtful design!

:::strapi Additional resources
* If you're searching for ways of replacing the default Rich text editor, please refer to the [corresponding page](/cms/admin-panel-customization/wysiwyg-editor).
* The <ExternalLink to="https://design-system.strapi.io/?path=/docs/getting-started-welcome--docs" text="Strapi Design System documentation"/> also provide extensive additional information on developing for Strapi's admin panel.
:::

<HotReloading />
