---
title: CLI
description: >-
  Fast-track local install for getting Strapi running on your computer in less
  than a minute.
displayed_sidebar: cmsSidebar
sidebar_label: CLI
tags:
  - installation
  - Command Line Interface (CLI)
  - database
  - MySQL
  - PostgreSQL
pagination_prev: cms/installation
pagination_next: cms/installation/docker
---

# CLI installation

This page explains how to install Strapi using the Command Line Interface (CLI).

## Prerequisites

import InstallPrerequisites from '/docs/snippets/installation-prerequisites.md'

<InstallPrerequisites components={props.components} />

## Installation

Use your preferred package manager to run one of the following commands:

<Tabs groupId="yarn-npm-pnpm">

<TabItem value="yarn" label="Yarn">

```bash
yarn create strapi-app my-project
```

</TabItem>

<TabItem value="npm" label="NPM">

```bash
npx create-strapi-app@latest my-project
```

</TabItem>

<TabItem value="pnpm" label="PNPM">

```bash
pnpm create strapi-app my-project
```

</TabItem>

</Tabs>

## CLI installation options

The `create-strapi-app` command can take the following options:

| Option                | Description                                                                                                                            |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| `--no-run`            | Prevent Strapi from automatically starting the application after initial build                                                          |
| `--use-npm`           | Force usage of npm instead of yarn to create the project                                                                                |
| `--debug`             | Display database connection error                                                                                                       |
| `--quickstart`        | Directly create the project without being prompted for input                                                                            |
| `--dbclient`          | Specify a database client (can be `sqlite`, `postgres`, `mysql`)                                                                        |
| `--dbhost`            | Database host                                                                                                                           |
| `--dbport`            | Database port                                                                                                                           |
| `--dbname`            | Database name                                                                                                                           |
| `--dbusername`        | Database username                                                                                                                       |
| `--dbpassword`        | Database password                                                                                                                       |
| `--dbssl`             | Use SSL database connection (available only for postgres)                                                                               |
| `--dbfile`            | Database file path for sqlite                                                                                                           |
| `--dbforce`           | Overwrite database content if any                                                                                                       |
| `--template`          | Specify a Strapi template to use for your project [See templates](#templates)                                                           |
| `--typescript`        | Create a TypeScript project (see [TypeScript development](/cms/typescript) documentation for details)                                  |

:::tip
You can also run `create-strapi-app --help` to see the list of available options.
:::

### Templates

A template is a pre-made Strapi configuration designed for a specific use case. It allows you to quickly bootstrap a custom Strapi project. Templates can be:

- A GitHub repository name, like `strapi/template-blog`
- A GitHub repository URL, like `https://github.com/strapi/template-blog.git`
- A local path to a folder, like `./my-template-folder`

:::note
To create a Strapi project with a template, use the `--template` option:

```bash
npx create-strapi-app@latest my-project --template blog
```

The previous command creates a Strapi project using the [web-blog template](https://github.com/strapi/templates/tree/main/packages/templates/blog).
:::

## What's next?

After installing Strapi, you can:

- [Configure your Strapi project](/cms/configurations) to fit your needs.
- [Develop your first custom plugin](/cms/plugins-development/create-a-plugin).
- [Deploy your Strapi project](/cms/deployment) to make it publicly available.
