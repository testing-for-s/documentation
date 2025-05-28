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

The Content History feature allows you to browse and restore previous versions of your content entries directly from the Content Manager.

## Usage

### Viewing Content History

To view the history of a content entry:

1. Navigate to the Content Manager
2. Select the content-type you want to view the history for
3. Click on an entry to open its edit view
4. Click on the "History" tab in the right sidebar

You will see a list of previous versions of the entry, including:

- The date and time the version was created
- The user who made the changes
- The type of action (e.g. create, update, publish)

### Comparing Versions

To compare two versions:

1. Select a version from the history list
2. Click the "Compare" button
3. Choose another version to compare against

The comparison view will highlight the differences between the two versions.

### Restoring a Previous Version

To restore a previous version:

1. Select the version you want to restore from the history list
2. Click the "Restore" button
3. Confirm the restoration

The entry will be reverted to the selected version. A new version will be created to record this restoration action.

### Configuration

By default, Strapi stores content history versions indefinitely. To configure a retention period:

1. Open your Strapi project
2. Navigate to `./config/plugins.js` (or create it if it doesn't exist)
3. Add the following configuration:

```javascript
module.exports = ({ env }) => ({
  'content-history': {
    enabled: true,
    config: {
      retentionDays: 30 // Retain versions for 30 days
    }
  }
});
```

Adjust the `retentionDays` value as needed. Versions older than this period will be automatically deleted.

:::note
Content history tables are now persisted to avoid data loss when users temporarily don't have a license.
:::