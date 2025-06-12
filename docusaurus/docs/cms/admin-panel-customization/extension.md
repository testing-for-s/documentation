---
title: Admin panel extension
displayed_sidebar: cmsSidebar
description: Learn more about extending Strapi's admin panel.
tags:
  - admin panel
  - admin panel customization
toc_max_heading_level: 4
---

# Extension

The Extension feature allows you to customize various aspects of the Strapi admin panel, enhancing its functionality and appearance to better suit your project's needs.

## Overview

Extensions provide a way to add new features, modify existing ones, or change the look and feel of the admin panel. This can be done by creating custom components, injecting new routes, or overriding default behaviors.

## Types of Extensions

There are several types of extensions you can create:

1. **UI Extensions**: Modify the appearance of the admin panel.
2. **Feature Extensions**: Add new functionality to the admin panel.
3. **Plugin Extensions**: Extend or override existing plugin behaviors.

## Creating an Extension

To create an extension, you'll need to follow these general steps:

1. Create a new directory for your extension in the `./src/admin/extensions` folder.
2. Implement your extension logic using React components and Strapi's API.
3. Register your extension in the admin panel configuration.

### Example: Creating a Simple UI Extension

Here's a basic example of how to create a UI extension that adds a custom welcome message to the admin panel:

1. Create a new file `./src/admin/extensions/components/WelcomeMessage.js`:

```javascript
import React from 'react';
import { Box, Typography } from '@strapi/design-system';

const WelcomeMessage = () => {
  return (
    <Box padding={4} background="neutral100">
      <Typography variant="beta">Welcome to your customized admin panel!</Typography>
    </Box>
  );
};

export default WelcomeMessage;
```

2. Register the extension in `./src/admin/app.js`:

```javascript
import WelcomeMessage from './extensions/components/WelcomeMessage';

export default {
  bootstrap(app) {
    app.injectContentManagerComponent('HomePage', 'before-content', {
      name: 'custom-welcome-message',
      Component: WelcomeMessage,
    });
  },
};
```

This example will inject a custom welcome message component at the top of the admin panel's homepage.

## Best Practices

When creating extensions, keep the following best practices in mind:

1. **Performance**: Ensure your extensions don't negatively impact the admin panel's performance.
2. **Consistency**: Try to maintain consistency with Strapi's existing design patterns and user experience.
3. **Modularity**: Keep your extensions modular and focused on specific functionality.
4. **Documentation**: Document your extensions well, especially if they're intended for use by other team members or the community.

## Advanced Extension Techniques

For more complex customizations, you can leverage Strapi's advanced extension capabilities:

### Overriding Plugin Components

You can override existing plugin components to change their behavior or appearance:

```javascript
export default {
  bootstrap(app) {
    app.overridePlugin('content-type-builder', 'components', {
      'attribute-list': {
        'list.deleteModalTitle': {
          id: 'custom.attribute.delete.title',
          defaultMessage: 'Are you sure you want to delete this field?',
        },
      },
    });
  },
};
```

### Adding Custom API Endpoints

For extensions that require backend functionality, you can add custom API endpoints:

1. Create a new controller in `./src/api/custom-extension/controllers/custom-extension.js`:

```javascript
module.exports = {
  async customAction(ctx) {
    // Your custom logic here
    ctx.body = { message: 'Custom action executed successfully' };
  },
};
```

2. Add a new route in `./src/api/custom-extension/routes/custom-extension.js`:

```javascript
module.exports = {
  routes: [
    {
      method: 'GET',
      path: '/custom-extension/action',
      handler: 'custom-extension.customAction',
      config: {
        policies: [],
      },
    },
  ],
};
```

## Conclusion

Extensions provide a powerful way to tailor the Strapi admin panel to your specific needs. By following the guidelines and examples provided in this documentation, you can create custom extensions that enhance the functionality and user experience of your Strapi application.

For more detailed information on specific extension types and advanced usage, refer to the official Strapi plugin development documentation.
