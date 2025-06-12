---
title: Configuration
displayed_sidebar: cloudSidebar
description: Configure your Strapi Cloud project settings and options.
canonicalUrl: https://docs.strapi.io/cloud/user-docs/configuration.html
tags:
- configuration
- settings
- Strapi Cloud
- Strapi Cloud project
---

# Configuration

This page provides an overview of the configuration options available for your Strapi Cloud project.

## GitHub App Integration

Strapi Cloud integrates with GitHub through a GitHub App to enable certain workflows and functionality. The current configuration includes:

- User documentation workflows: The `generateUserDocs` workflow is enabled for generating user documentation.
- Issues: GitHub Issues are enabled for the project.

### User Documentation Workflow

The `generateUserDocs` workflow allows you to automatically generate and update user documentation for your Strapi Cloud project. This workflow can be triggered on certain events like pushes to specific branches or creation of pull requests.

To configure this workflow:

1. Navigate to your project settings
2. Go to the "Workflows" section  
3. Enable the "Generate User Docs" workflow
4. Configure any workflow settings like trigger events or branch filters

### GitHub Issues

With GitHub Issues enabled, you can use the integrated issue tracking functionality directly within your Strapi Cloud project. This allows you to:

- Create and manage issues related to your project
- Assign issues to team members
- Track progress on issues
- Link issues to code changes and pull requests

To access GitHub Issues for your project:

1. Go to your project dashboard
2. Click on the "Issues" tab
3. You can now view existing issues or create new ones

## Additional Configuration

For more advanced configuration options, refer to the following documentation pages:

- [Project Settings](/cloud/projects/settings) - General project configuration 
- [Environment Variables](/cloud/projects/settings#environment-variables) - Configure environment-specific settings
- [Custom Domains](/cloud/projects/settings#connecting-a-custom-domain) - Set up custom domains for your project

If you need any assistance with configuring your Strapi Cloud project, please don't hesitate to reach out to our support team.