---
title: Quick Start Guide - Strapi Developer Docs
description: >-
  Get ready to get Strapi, your favorite open-source headless cms up and running
  in less than 3 minutes.
displayed_sidebar: cmsSidebar
pagination_prev: index
pagination_next: quickstart/next-steps
tags:
  - guides
  - Content-type Builder
  - collection type
  - Content Manager
  - Strapi Cloud
sidebar_label: Quick Start Guide
sidebar_position: 2
---

# Quick Start

This Quick Start guide will help you create your first Strapi project and familiarize you with the basics of Strapi.

## Prerequisites

Before you start, make sure you have:

<SnippetInstallationPrerequisites components={props.components} />

## Creating a Strapi Project

To create your first Strapi project, follow these steps:

1. In a terminal, run the following command:

<Tabs groupId="yarn-npm">

<TabItem value="npm" label="NPM">

```bash
npx create-strapi-app@latest my-project
```

</TabItem>

<TabItem value="yarn" label="Yarn">

```bash
yarn create strapi-app my-project
```

</TabItem>

</Tabs>

2. Choose your preferred installation type:
   - `Quickstart (recommended)`: Creates a project with a default SQLite database.
   - `Custom (manual settings)`: Allows you to choose your preferred database and customize other options.

3. Wait for the installation to complete and your Strapi application to start.

## Accessing the Admin Panel

Once your Strapi application is running:

1. Open your web browser and go to [http://localhost:1337/admin](http://localhost:1337/admin).
2. Create your first admin user by filling out the registration form.
3. You're now logged in to the Strapi admin panel!

## Creating Content

Let's create some basic content:

1. In the admin panel, click on "Content-Type Builder" in the left sidebar.
2. Click "Create new collection type".
3. Name it "Restaurant" and add the following fields:
   - Name (Text)
   - Description (Rich Text)
   - Open (Boolean)
4. Save your changes and wait for Strapi to restart.
5. Click on "Content Manager" in the left sidebar.
6. Click "Create new entry" under the Restaurant collection type.
7. Fill in the details for your first restaurant and publish it.

## Accessing Your API

Strapi automatically generates a REST API for your content. To access it:

1. Ensure your Strapi application is running.
2. Open a new browser tab and go to [http://localhost:1337/api/restaurants](http://localhost:1337/api/restaurants).
3. You should see a JSON response with your restaurant data.

## What's Next?

Congratulations! You've created your first Strapi project, added some content, and accessed your API. Here are some next steps to explore:

- Learn more about [Content-Types and Fields](/cms/concepts/content-types)
- Explore [Roles and Permissions](/cms/concepts/rbac)
- Set up [Strapi in a production environment](/cms/deployment/hosting-guides/hosting-guides-intro)

For more detailed information and advanced topics, browse through our documentation or join our [community forums](https://forum.strapi.io) for support and discussions.
