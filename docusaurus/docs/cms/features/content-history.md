---
title: Content History
description: Learn how you can use the Content History feature of Strapi 5 to browse and restore previous versions of documents from the Content Manager.
displayed_sidebar: cmsSidebar
toc_max_heading_level: 5
tags:
 - content manager
 - content history
 - features
---

# Content History

The Content History feature in Strapi 5 allows you to browse and restore previous versions of documents from the Content Manager. This feature helps you track changes, review past versions, and revert to earlier states of your content when needed.

:::note
Content history tables are now persisted to avoid data loss when users temporarily don't have a license.
:::

## Usage

The Content History feature provides the following functionality:

### Viewing version history

1. Navigate to the Content Manager and select a content-type.
2. Open an entry by clicking on it in the list view.
3. In the right sidebar, click on the "History" tab to view the version history of the document.

The history tab displays a list of all previous versions of the document, including:
- The date and time of each version
- The user who made the changes
- A brief summary of the changes made

### Comparing versions

To compare two versions of a document:

1. In the History tab, select two versions you want to compare.
2. Click the "Compare" button.
3. A diff view will appear, highlighting the differences between the two selected versions.

### Restoring previous versions

To restore a previous version of a document:

1. In the History tab, find the version you want to restore.
2. Click the "Restore" button next to that version.
3. Confirm the restoration in the dialog that appears.

The document will be reverted to the selected version, and a new version will be created to record this change.

### Automatic version creation

Strapi automatically creates new versions of a document when:

- A new document is created
- An existing document is updated
- A document is published or unpublished
- A draft is discarded

This ensures that you have a comprehensive history of all changes made to your content.

### Retention period

By default, Strapi keeps historical versions for a certain period. The retention period can be configured in your Strapi application settings. After this period, older versions are automatically deleted to manage database size.

:::tip
You can customize the retention period based on your project's needs and storage capabilities.
:::

## Configuration

The Content History feature is enabled by default in Strapi 5. However, you can configure certain aspects of its behavior:

### Adjusting the retention period

To change the retention period for historical versions:

1. Open your Strapi project's configuration files.
2. Locate the Content History configuration (usually in `./config/plugins.js` or a similar file).
3. Set the `retentionDays` value to your desired number of days:

```javascript
module.exports = ({ env }) => ({
  // ... other plugin configs
  'content-history': {
    enabled: true,
    config: {
      retentionDays: 30 // Adjust this value as needed
    }
  },
  // ... other plugin configs
});
```

### Disabling Content History for specific content-types

If you want to disable Content History for certain content-types:

1. Open the configuration file for the specific content-type.
2. Add the `historyEnabled` option and set it to `false`:

```javascript
module.exports = {
  kind: 'collectionType',
  collectionName: 'articles',
  info: {
    singularName: 'article',
    pluralName: 'articles',
    displayName: 'Article',
  },
  options: {
    draftAndPublish: true,
    historyEnabled: false, // Disable Content History for this content-type
  },
  // ... rest of your content-type configuration
};
```

By leveraging the Content History feature, you can maintain better control over your content's evolution, easily track changes, and recover from unintended modifications when necessary.