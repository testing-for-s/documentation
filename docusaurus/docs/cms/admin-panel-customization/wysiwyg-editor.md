---
title: Customizing the rich text editor
description: >-
  Learn more about the various strategies available to customize the WYSIWYG
  editor in Strapi's admin panel.
displayed_sidebar: cmsSidebar
tags:
  - admin panel
  - admin panel customization
  - WYSIWYG editor
sidebar_label: Rich text editor
---

# WYSIWYG Editor

The WYSIWYG (What You See Is What You Get) editor is a powerful tool available in the Strapi admin panel that allows content creators to easily format and style their content without needing to write HTML or use complex markup.

## Overview

The WYSIWYG editor is available for rich text fields in your content types. It provides a user-friendly interface for creating formatted content, including headings, lists, links, images, and more.

<ThemedImage
  alt="WYSIWYG Editor in Strapi Admin Panel"
  sources={{
    light: '/img/assets/content-manager/wysiwyg-editor-light.png',
    dark: '/img/assets/content-manager/wysiwyg-editor-dark.png',
  }}
/>

## Features

The WYSIWYG editor includes the following features:

- Text formatting (bold, italic, underline)
- Headings (H1-H6)
- Lists (ordered and unordered)
- Links
- Images
- Blockquotes
- Code blocks
- Horizontal rules

## Using the WYSIWYG Editor

To use the WYSIWYG editor:

1. Navigate to the Content Manager in your Strapi admin panel.
2. Create or edit an entry that contains a rich text field.
3. Click on the rich text field to activate the WYSIWYG editor.
4. Use the toolbar at the top of the editor to format your content.

## Customizing the WYSIWYG Editor

Strapi allows you to customize the WYSIWYG editor to fit your specific needs. You can add or remove features, change the toolbar layout, or even replace the default editor with a different one.

To customize the WYSIWYG editor, you'll need to modify your Strapi project's code. Here's an example of how to customize the toolbar options:

```javascript
// path: ./src/admin/app.js

import { Wysiwyg } from '@strapi/plugin-wysiwyg';

export default {
  config: {
    // ...
    wysiwyg: {
      options: {
        toolbar: [
          'bold',
          'italic',
          'underline',
          'link',
          'bullist',
          'numlist',
          'image',
        ],
      },
    },
  },
  bootstrap(app) {
    app.registerComponent({
      name: 'wysiwyg',
      Component: Wysiwyg,
    });
  },
};
```

In this example, we're customizing the toolbar to only include basic formatting options, lists, links, and images.

## Best Practices

When using the WYSIWYG editor, consider the following best practices:

1. Keep your content structure consistent across entries.
2. Use headings to create a clear hierarchy in your content.
3. Avoid overusing formatting options, as this can make your content harder to read.
4. Consider accessibility when adding images by including alt text.

By following these guidelines and leveraging the power of the WYSIWYG editor, you can create rich, well-formatted content that enhances the user experience of your Strapi-powered application.
