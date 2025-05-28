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

The WYSIWYG (What You See Is What You Get) editor in Strapi's admin panel can be customized to fit your specific needs. This document outlines the various strategies available for customizing the editor.

## Customizing the Blocks toolbar

The Blocks toolbar in the WYSIWYG editor can be customized by modifying the `BlocksToolbar` component. Here's an overview of how the toolbar is structured and can be customized:

### Toolbar Structure

The `BlocksToolbar` component is composed of several parts:

1. `BlocksDropdown`: Allows users to select different block types.
2. Modifier buttons: For text formatting (bold, italic, etc.).
3. `LinkButton`: For adding links.
4. List buttons: For creating ordered and unordered lists.

### Customizing Toolbar Items

You can customize the toolbar by modifying the `observedComponents` array in the `BlocksToolbar` component. This array determines which items appear in the toolbar and in what order.

```javascript
const observedComponents: ObservedComponent[] = [
  // Modifier buttons
  ...Object.entries(modifiers).map(([name, modifier]) => {
    // ... (code for modifier buttons)
  }),
  // Link button
  {
    toolbar: <LinkButton disabled={isButtonDisabled} location="toolbar" />,
    menu: <LinkButton disabled={isButtonDisabled} location="menu" />,
    key: 'block.link',
  },
  // List buttons
  {
    toolbar: (
      <Flex direction="row">
        <ToolbarSeparator style={{ marginLeft: '0.4rem' }} />
        <Toolbar.ToggleGroup type="single" asChild>
          <Flex gap={1}>
            <ListButton block={blocks['list-unordered']} format="unordered" location="toolbar" />
            <ListButton block={blocks['list-ordered']} format="ordered" location="toolbar" />
          </Flex>
        </Toolbar.ToggleGroup>
      </Flex>
    ),
    menu: (
      <>
        <Menu.Separator />
        <ListButton block={blocks['list-unordered']} format="unordered" location="menu" />
        <ListButton block={blocks['list-ordered']} format="ordered" location="menu" />
      </>
    ),
    key: 'block.list',
  },
];
```

### Styling the Toolbar

The toolbar's appearance can be customized using styled components. For example:

```javascript
const ToolbarWrapper = styled<FlexComponent>(Flex)`
  &[aria-disabled='true'] {
    cursor: not-allowed;
    background: ${({ theme }) => theme.colors.neutral150};
  }
`;

const ToolbarSeparator = styled(Toolbar.Separator)`
  background: ${({ theme }) => theme.colors.neutral150};
  width: 1px;
  height: 2.4rem;
  margin-left: 0.8rem;
  margin-right: 0.8rem;
`;

const FlexButton = styled<FlexComponent<'button'>>(Flex)`
  // Inherit the not-allowed cursor from ToolbarWrapper when disabled
  &[aria-disabled] {
    cursor: not-allowed;
  }

  &[aria-disabled='false'] {
    cursor: pointer;

    // Only apply hover styles if the button is enabled
    &:hover {
      background: ${({ theme }) => theme.colors.primary100};
    }
  }
`;
```

## Adding Custom Blocks

To add custom blocks to the WYSIWYG editor, you can extend the `blocks` object in the `BlocksEditor` component. Each block should define its own conversion logic, icon, and label.

For example, to add a new block type:

```javascript
const blocks = {
  // ... existing blocks
  'custom-block': {
    icon: CustomBlockIcon,
    label: { id: 'components.Blocks.customBlock', defaultMessage: 'Custom Block' },
    handleConvert: (editor) => {
      // Custom conversion logic
    },
    matchNode: (node) => node.type === 'custom-block',
  },
};
```

## Customizing Conversion Modals

When converting between block types, you can provide custom modal components to handle more complex conversions. The `useConversionModal` hook can be used to manage these modals:

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

## Extending Editor Functionality

To extend the editor's functionality, you can create custom plugins or modify existing ones. The `BlocksEditor` component uses the `useBlocksEditorContext` hook to provide editor context throughout the component tree.

For example, to add a custom plugin:

```javascript
import { Plugin } from 'slate-react';

const customPlugin: Plugin = {
  onKeyDown(event, editor, next) {
    // Custom key handling logic
  },
  // ... other plugin methods
};

// Add the plugin to the editor
const plugins = [...defaultPlugins, customPlugin];
```

Remember to test your customizations thoroughly to ensure they work well with the existing editor functionality and don't introduce any conflicts or performance issues.

By leveraging these customization options, you can tailor the WYSIWYG editor to better suit your project's specific requirements while maintaining consistency with Strapi's admin panel design.