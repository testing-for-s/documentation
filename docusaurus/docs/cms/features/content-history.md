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

The Content History feature allows you to browse and restore previous versions of documents from the Content Manager.

## Usage

### Viewing content history

To view the history of a document:

1. Navigate to the Content Manager
2. Select the content type you want to view
3. Click on a specific entry
4. In the right sidebar, click on the "History" tab

This will display a list of previous versions of the document, including:

- The date and time the version was created
- The user who made the changes
- A summary of what changed

### Restoring previous versions

To restore a previous version:

1. View the content history as described above
2. Find the version you want to restore
3. Click the "Restore" button next to that version

This will revert the document to that previous state. A new version will be created to track this restoration.

## Configuration

Content History is enabled by default for all content types. The feature utilizes database tables with the prefix `strapi_history_versions` to store version data.

:::note
Content History data is subject to retention policies. By default, versions are kept for 30 days before being automatically deleted.
:::

### Customizing retention

You can customize the retention period by modifying the `createLifecyclesService` function in your project:

```javascript
// In config/functions/bootstrap.js

module.exports = () => {
  const retentionDays = 60; // Change this value to set custom retention

  strapi.services['content-history'].setRetentionDays(retentionDays);
};
```

## Persistence of history tables

As of Strapi 5, history tables are now persisted even if a user temporarily doesn't have a valid license. This helps prevent potential data loss scenarios.

The relevant code snippet from `lifecycles.ts`:

```typescript
await persistTablesWithPrefix('strapi_history_versions');
```

This ensures that content history data is maintained consistently.

## Additional considerations

- Content History versions are created for create, update, clone, publish, unpublish, and discard draft actions.
- For localized content types, versions are created for each locale separately.
- The feature respects Draft & Publish status, creating versions appropriately for both draft and published states.

By leveraging Content History, you can confidently manage your content with the ability to review and revert changes as needed.