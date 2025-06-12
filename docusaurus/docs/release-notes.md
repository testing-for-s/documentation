---
title: Release notes
description: >-
  Learn what has changed with each version of the Strapi 5 documentation, with
  links to GitHub pull requests for more information.
toc_max_heading_level: 2
custom_edit_url: null
---

<div className="release-notes-page">

This page lists all the Strapi Docs version numbers and their corresponding updates.

<details>
<summary><Icon name="graduation-cap" /> Strapi Docs version numbers explained:</summary>

The **Strapi Documentation** (Strapi Docs) at [docs.strapi.io](https://docs.strapi.io) **always documents the latest version of Strapi (CMS and Cloud) products**.

Since Strapi Docs version 5.0.0, the **docs' version number is independent from the Strapi product version**. Thus, the version numbers of <ExternalLink to="https://github.com/strapi/documentation" text="strapi/documentation"/> and <ExternalLink to="https://github.com/strapi/strapi" text="strapi/strapi"/> may differ.

Strapi Docs now follow the **<ExternalLink to="https://semver.org/" text="semantic versioning"/>** philosophy, but adapted to docs:

- **Major version** (6.0.0, 7.0.0…): A **significant rewrite** of the docs (content or framework). This may impact the user experience, redesign the site, or break old links (redirections are handled, but broken links can be <ExternalLink to="https://github.com/strapi/documentation/issues/new/choose" text="reported"/>).
- **Minor version** (5.1.0, 5.2.0…): **New Strapi features** or improvements to the docs (e.g., new components or tools).
- **Patch version** (5.1.1, 5.1.2…): **Content updates**, including improvement or extension of existing pages, code examples fixes, and typos.

New versions (minor or patch) are generally released weekly, on Wednesdays.
<br/>

</details>

## 6.5.0

<br />
### <Icon name='sparkle' /> New content

<br />

#### Repository
- [Add LLMs.txt and LLMs-full.txt generation](https://github.com/strapi/documentation/pull/2507)

We've started adding <ExternalLink to="https://llmstxt.org/" text="llms.txt"/> support to the Strapi Docs. You can find the files in the footer or access them directly via the following links:
- [`llms.txt`](https://docs.strapi.io/llms.txt)
- [`llms-full.txt`](https://docs.strapi.io/llms-full.txt)

![LLM files in the footer](/img/assets/llms/llms-footer.png)

### <Icon name='pen-nib' /> Updated content

<br />

#### CMS
- [Update app creation flow to include Growth free trial](https://github.com/strapi/documentation/pull/2496)

### <Icon name='broom' /> Chore, fixes, typos, and other improvements

<br />

#### CMS
- [Admin Panel API typo in example](https://github.com/strapi/documentation/pull/2508)

***
This release was made possible thanks to the following contributors. Thank you! 🫶
<div>
<a href="https://github.com/abdallahmz" target="_blank">
    <img className="no-zoom" src="https://avatars.githubusercontent.com/u/55555555?v=4" width="40" height="40" style={{borderRadius: '50%'}} alt="abdallahmz"/>
</a>
<a href="https://github.com/martinschilliger" target="_blank">
    <img className="no-zoom" src="https://avatars.githubusercontent.com/u/66666666?v=4" width="40" height="40" style={{borderRadius: '50%'}} alt="martinschilliger"/>
</a>
<a href="https://github.com/pwizla" target="_blank">
    <img className="no-zoom" src="https://avatars.githubusercontent.com/u/77777777?v=4" width="40" height="40" style={{borderRadius: '50%'}} alt="pwizla"/>
</a>
</div>
<br/>
<br/>

## 6.4.0

This release marks some significant additions and rewrites. We've rethought the dev-related content in the CMS docs, with a **clearer table of contents** for the development, configuration, and customization aspects of Strapi.

We've also added a handy **<Icon name="copy"/> Copy Markdown** button to the navigation bar on the right, so you can easily copy & paste raw Markdown content from the page into your favorite LLM!

Enjoy, and watch out for more AI-related features soon 👀

<br />

### <Icon name='sparkle' /> New content

<br />

#### Repository
- [Add "Copy Markdown" button](https://github.com/strapi/documentation/pull/2498)

### <Icon name='pen-nib' /> Updated content

<br />

#### CMS
- [Dev-related content rework, iteration #2 (admin panel configuration and customization)](https://github.com/strapi/documentation/pull/2505)
- [Dev-related content rework, iteration #1](https://github.com/strapi/documentation/pull/2501)
- [Content-type Builder revamp (stable release)](https://github.com/strapi/documentation/pull/2480)

### <Icon name='broom' /> Chore, fixes, typos, and other improvements

<br />

#### CMS
- [Cloud docs typo fixes](https://github.com/strapi/documentation/pull/2500)

***
This release was made possible thanks to the following contributors. Thank you! 🫶
<div>
<a href="https://github.com/mariekirsch" target="_blank">
    <img className="no-zoom" src="https://avatars.githubusercontent.com/u/88888888?v=4" width="40" height="40" style={{borderRadius: '50%'}} alt="mariekirsch"/>
</a>
<a href="https://github.com/meganelacheny" target="_blank">
    <img className="no-zoom" src="https://avatars.githubusercontent.com/u/99999999?v=4" width="40" height="40" style={{borderRadius: '50%'}} alt="meganelacheny"/>
</a>
<a href="https://github.com/pwizla" target="_blank">
    <img className="no-zoom" src="https://avatars.githubusercontent.com/u/77777777?v=4" width="40" height="40" style={{borderRadius: '50%'}} alt="pwizla"/>
</a>
</div>
<br/>
<br/>

<!-- The rest of the content remains unchanged -->
