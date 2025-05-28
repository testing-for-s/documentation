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

Content History keeps track of changes made to your content over time. You can view the history of a document, compare different versions, and restore previous versions if needed.

### Viewing Content History

To view the history of a document:

1. Navigate to the Content Manager
2. Open the document you want to view the history for
3. Click on the "History" tab

This will display a list of all previous versions of the document, including the date and time they were created.

### Comparing Versions

You can compare different versions of a document to see what changes were made:

1. In the History tab, select two versions you want to compare
2. Click the "Compare" button

This will show a side-by-side view highlighting the differences between the two versions.

### Restoring Previous Versions

To restore a previous version of a document:

1. In the History tab, find the version you want to restore
2. Click the "Restore" button next to that version

This will create a new version of the document with the content from the selected previous version.

## Configuration

Content History is enabled by default for all content types. The feature uses data persistence to ensure that historical versions are not lost, even if a user temporarily doesn't have a license.

### Retention Period

By default, Content History versions are kept for 30 days. You can configure this retention period in your Strapi configuration:

```javascript
module.exports = ({ env }) => ({
  contentHistory: {
    retentionDays: 60, // Set retention to 60 days
  },
});
```

### Data Persistence

Content History uses data persistence to prevent data loss. This is handled automatically by Strapi and doesn't require any additional configuration from users.

## Limitations

- Content History is not available for components or dynamic zones.
- The number of versions stored may impact database size over time, especially for large content types or frequent updates.

By leveraging Content History, you can maintain a comprehensive record of your content's evolution, easily track changes, and revert to previous versions when necessary.