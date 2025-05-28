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

The WYSIWYG (What You See Is What You Get) editor in Strapi's admin panel can be customized to fit your specific needs. This document outlines the various strategies available for customization.

## Blocks Toolbar Customization

The Blocks Toolbar component in the WYSIWYG editor can be customized to add, remove, or modify the available formatting options. Here's an example of how the `BlocksToolbar` component is structured:

```jsx
const BlocksToolbar = () => {
  const { editor, blocks, modifiers, disabled } = useBlocksEditorContext('BlocksToolbar');
  const { formatMessage } = useIntl();

  const checkButtonDisabled = () => {
    // Disable buttons when an image is selected or when the editor is disabled
    if (disabled) {
      return true;
    }

    if (!editor.selection) {
      return false;
    }

    const selectedNode = editor.children[editor.selection.anchor.path[0]];

    if (['image', 'code'].includes(selectedNode.type)) {
      return true;
    }

    return false;
  };

  const isButtonDisabled = checkButtonDisabled();

  // ... rest of the component code
};
```

This component uses the `useBlocksEditorContext` hook to access the editor state and configuration. It also checks if buttons should be disabled based on the current selection and editor state.

## Adding Custom Blocks

You can add custom blocks to the WYSIWYG editor by extending the `blocks` object. Here's an example of how you might add a custom block:

```javascript
const customBlocks = {
  ...blocks,
  'custom-block': {
    icon: CustomBlockIcon,
    label: {
      id: 'components.Blocks.custom',
      defaultMessage: 'Custom Block',
    },
    isInBlocksSelector: true,
    handleConvert: (editor) => {
      // Custom conversion logic
    },
    matchNode: (node) => node.type === 'custom-block',
  },
};
```

## Customizing Existing Blocks

You can also modify existing blocks. For example, to customize the list buttons:

```jsx
const ListButton = ({ block, format, location = 'toolbar' }) => {
  const { editor, disabled, blocks } = useBlocksEditorContext('ListButton');
  const { formatMessage } = useIntl();

  const isListActive = () => {
    // Check if the current selection is a list of the specified format
  };

  const isListDisabled = () => {
    // Logic to determine if the list button should be disabled
  };

  const toggleList = (format) => {
    // Logic to toggle the list format
  };

  // Render the button based on location (toolbar or menu)
  // ...
};
```

## Styling the Toolbar

The toolbar can be styled using styled-components. Here's an example of how some components are styled:

```jsx
const ToolbarWrapper = styled<FlexComponent>(Flex)`
  &[aria-disabled='true'] {
    cursor: not-allowed;
    background: ${({ theme }) => theme.colors.neutral150};
  }
`;

const FlexButton = styled<FlexComponent<'button'>>(Flex)`
  &[aria-disabled] {
    cursor: not-allowed;
  }

  &[aria-disabled='false'] {
    cursor: pointer;

    &:hover {
      background: ${({ theme }) => theme.colors.primary100};
    }
  }
`;
```

## Handling Conversions

When converting between block types, you can handle special cases. For example, the `useConversionModal` hook is used to handle modal components that may be returned when converting a block:

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

## Internationalization

The WYSIWYG editor supports internationalization. You can use the `useIntl` hook to format messages:

```javascript
const { formatMessage } = useIntl();
const labelMessage = formatMessage(label);
```

## Accessibility

The WYSIWYG editor components are designed with accessibility in mind. For example, the toolbar buttons use `aria-disabled` and `aria-label` attributes:

```jsx
<Toolbar.ToggleItem
  value={name}
  data-state={isActive ? 'on' : 'off'}
  onMouseDown={(e) => {
    e.preventDefault();
    handleClick();
    ReactEditor.focus(editor);
  }}
  aria-disabled={disabled}
  disabled={disabled}
  aria-label={labelMessage}
  asChild
>
  {/* Button content */}
</Toolbar.ToggleItem>
```

By leveraging these customization options, you can tailor the WYSIWYG editor to better suit your project's needs while maintaining the core functionality and accessibility features provided by Strapi.