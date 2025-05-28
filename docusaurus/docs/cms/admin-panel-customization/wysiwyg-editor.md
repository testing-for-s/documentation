---
title: Customizing the WYSIWYG editor
description: Learn more about the various strategies available to customize the WYSIWYG editor in Strapi's admin panel.
displayed_sidebar: cmsSidebar
sidebar_label: Rich text editor
tags:
- admin panel 
- admin panel customization
- WYSIWYG editor
---

# Customizing the WYSIWYG editor

Strapi's admin panel includes a WYSIWYG (What You See Is What You Get) editor that allows content managers to easily create and edit rich text content. This editor can be customized to fit your specific needs.

## BlocksToolbar component

The `BlocksToolbar` component is responsible for rendering the toolbar of the WYSIWYG editor. It provides various options for formatting and structuring content.

### Key features

- **Block selection**: Allows users to choose different block types (e.g., paragraph, headings, lists).
- **Text formatting**: Provides options for bold, italic, and other text styles.
- **Link insertion**: Enables users to add and edit links within the content.
- **List creation**: Supports both ordered and unordered lists.

### Customization options

You can customize the `BlocksToolbar` by modifying its subcomponents or extending its functionality. Some customization possibilities include:

- Adding new block types
- Customizing the appearance of toolbar buttons
- Implementing custom formatting options

## Conversion modal

The WYSIWYG editor includes a conversion modal that allows users to convert content between different block types.

```javascript
function useConversionModal() {
  const [modalElement, setModalComponent] = React.useState<React.JSX.Element | null>(null);

  const handleConversionResult = (renderModal: void | (() => React.JSX.Element) | undefined) => {
    if (renderModal) {
      setModalComponent(React.cloneElement(renderModal(), { key: Date.now() }));
    }
  };

  return { modalElement, handleConversionResult };
}
```

This modal can be customized to support additional conversion options or to modify the conversion behavior for existing block types.

## Toolbar buttons

The WYSIWYG editor's toolbar includes various buttons for different actions. These buttons can be customized or extended to add new functionality.

```javascript
const ToolbarButton = ({
  icon: Icon,
  name,
  label,
  isActive,
  disabled,
  handleClick,
}: ToolbarButtonProps) => {
  // ... (existing implementation)
};
```

You can create new toolbar buttons or modify existing ones to add custom actions or change their behavior.

## Block dropdown

The block dropdown allows users to select different block types for their content.

```javascript
const BlocksDropdown = () => {
  // ... (existing implementation)
};
```

You can customize this dropdown to add new block types or modify the behavior of existing ones.

## List handling

The WYSIWYG editor provides special handling for list blocks, including both ordered and unordered lists.

```javascript
const ListButton = ({ block, format, location = 'toolbar' }: ListButtonProps) => {
  // ... (existing implementation)
};
```

You can customize the list handling to support additional list types or modify the behavior of existing list formats.

## Link handling

The editor includes functionality for inserting and editing links within the content.

```javascript
const LinkButton = ({
  disabled,
  location = 'toolbar',
}: {
  disabled: boolean;
  location?: 'toolbar' | 'menu';
}) => {
  // ... (existing implementation)
};
```

You can customize the link handling to support additional link types or modify the link insertion and editing behavior.

## Extending the WYSIWYG editor

To extend or customize the WYSIWYG editor, you can:

1. Create a custom plugin that overrides or extends the default editor components.
2. Use the Strapi plugin extension system to modify the existing WYSIWYG editor plugin.
3. Implement custom blocks, formats, or toolbar actions by extending the existing components.

For more information on customizing Strapi's admin panel, refer to the [Admin Panel Customization](/cms/admin-panel-customization) documentation.