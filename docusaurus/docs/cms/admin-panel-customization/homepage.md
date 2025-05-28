# Homepage customization!!

The Homepage is the landing page of the Strapi admin panel. By default, it provides an overview of your content with 2 default widgets:

* *Last edited entries*: Displays recently modified content entries, including their content type, status, and when they were updated.

* *Last published entries*: Shows recently published content entries, allowing you to quickly access and manage your published content.

\<ThemdImage alt="Homepage with default widgets" sources={{ light: '/img/assets/admin-homepage/admin-panel-homepage.png', dark: '/img/assets/admin-homepage/admin-panel-homepage\_DARK.png', }} />

These default widgets cannot currently be removed, but you can customize the Homepage by creating your own widgets.

:::note If you recently created a Strapi project, the Homepage may also display a quick tour above widgets if you haven't skipped it yet. :::

## Adding custom widgets

To add a custom widget, you can:

* install a plugin from the Marketplace

* or create and register your own widgets

The present page will describe how to create and register your widgets.

### Registering custom widgets

To register a widget, use `app.widgets.register()`:

* in the plugin's `register` lifecycle method of the `index` file if you're building a plugin (recommended way),

* or in the application's global `register()` lifecycle method if you're adding the widget to just one Strapi application without a plugin.

:::info The examples on the present page will cover registering a widget through a plugin. Most of the code should be reusable if you register the widget in the application's global `register()` lifecycle method, except you should not pass the `pluginId` property. :::

:::note The API requires Strapi 5.13+ The `app.widgets.register` API only works with Strapi 5.13 and above. Trying to call the API with older versions of Strapi will crash the admin panel. Plugin developers who want to register widgets should either:

* set `^5.13.0` as their `@strapi/strapi` peerDependency in their plugin `package.json`. This peer dependency powers the Marketplace's compatibility check.

* or check if the API exists before calling it:

  ```js
  if ('widgets' in app) {
    // proceed with the registration
  }
  ```

The peerDependency approach is recommended if the whole purpose of the plugin is to register widgets. The second approach makes more sense if a plugin wants to add a widget but most of its functionality is elsewhere. :::

#### Widget API reference

The `app.widgets.register()` method can take either a single widget configuration object or an array of configuration objects. Each widget configuration object can accept the following properties:

PropertyTypeDescriptionRequired`iconReact.ComponentType`Icon component to display beside the widget titleYes`titleMessageDescriptor`Title for the widget with translation supportYes`component() => Promise<React.ComponentType>`Async function that returns the widget componentYes`idstring`Unique identifier for the widgetYes`linkObject`Optional link to add to the widget (see link object properties)No`pluginIdstring`ID of the plugin registering the widgetNo`permissionsPermission[]`Permissions required to view the widgetNo

**Link object properties:**

If you want to add a link to your widget (e.g., to navigate to a detailed view), you can provide a `link` object with the following properties:

PropertyTypeDescriptionRequired`labelMessageDescriptor`The text to display for the linkYes`hrefstring`The URL where the link should navigate toYes

### Creating a widget component

Widget components should be designed to display content in a compact and informative way.

Here's how to implement a basic widget component:

:::tip For simplicity, the example below uses data fetching directly inside a useEffect hook. While this works for demonstration purposes, it may not reflect best practices in production.

For more robust solutions, consider alternative approaches recommended in the React documentation. If you're looking to integrate a data fetching library, we recommend using TanStackQuery. :::

**Data management**:

The green box above represents the area where the user's React component (from `widget.component` in the API) is rendered. You can render whatever you like inside of this box. Everything outside that box is, however, rendered by Strapi. This ensures overall design consistency within the admin panel. The `icon`, `title`, and `link` (optional) properties provided in the API are used to display the widget.

#### Widget helper components reference

Strapi provides several helper components to maintain a consistent user experience across widgets:

ComponentDescriptionUsage`Widget.Loading`Displays a loading spinner and messageWhen data is being fetched`Widget.Error`Displays an error stateWhen an error occurs`Widget.NoData`Displays when no data is availableWhen the widget has no data to show`Widget.NoPermissions`Displays when user lacks required permissionsWhen the user cannot access the widget

These components help maintain a consistent look and feel across different widgets. You could render these components without children to get the default wording: `<Widget.Error />` or you could pass children to override the default copy and specify your own wording: `<Widget.Error>Your custom error message</Widget.Error>`.

## Widget placement and behavior

Once registered, custom widgets appear on the Strapi admin panel's Homepage below the default widgets. Widgets are displayed in a card-based layout, with each widget contained within its own card that includes:

* **Header section**: Contains the widget icon, title, and optional link (if provided in the registration)

* **Content area**: Where your custom React component is rendered

* **Consistent styling**: Automatically matches the admin panel's design system

### Widget visibility and permissions

Widgets respect Strapi's permission system. If you specify permissions in your widget registration using the `permissions` property, the widget will only be visible to users who have the required permissions. Users without the necessary permissions will see a `Widget.NoPermissions` state instead of the widget content.

### Widget ordering

Currently, custom widgets are displayed in the order they are registered. The two default widgets (*Last edited entries* and *Last published entries*) always appear first, followed by custom widgets in registration order. Widget positioning and custom ordering options may be enhanced in future versions of Strapi.

### Adding widgets to the sidebar

While this documentation focuses on Homepage widgets, it's worth noting that widgets in Strapi are specifically designed for the Homepage dashboard. If you're looking to add custom navigation or functionality to the sidebar, you should instead consider:

* **Menu links**: Use `app.addMenuLink()` to add custom navigation items to the main sidebar menu

* **Injection zones**: Use `app.addFields()` or other injection zone APIs to add content to specific areas of existing pages

* **Custom pages**: Create entirely new pages within your plugin that can be accessed through sidebar navigation

For more information on sidebar customization and navigation, refer to the plugin development documentation and admin panel customization guides.

## Example: Adding a content metrics widget

The following is a complete example of how to create a content metrics widget that displays the number of entries for each content type in your Strapi application.

The end result will look like the following in your admin panel's Homepage:

\<ThemedImage alt="Content metrics widget showing content type counts" sources={{ light: '/img/assets/homepage-customization/content-metrics-widget.png', dark: '/img/assets/homepage-customization/content-metrics-widget\_DARK.png', }} />

The widget shows counts for example content-types automatically generated by Strapi when you provide the `--example` flag on installation (see CLI installation options for details).

This widget can be added to Strapi by:

1. creating a "content-metrics" plugin (see plugin creation documentation for details)

2. re-using the code examples provided below.

:::tip If you prefer a hands-on approach, you can reuse the following . :::
