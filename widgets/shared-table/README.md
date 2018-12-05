# Common Table Settings

## Overview

The **Common Table Settings** are inherited by [Table](../series-table/README.md), [Property](../property-table/README.md), and [Console](../alert-table/README.md) widgets.

## Widget Settings

* The settings apply to the `[widget]` section.

Name | Description | &nbsp;
:--|:--|:--
<a name="show-tag-names"></a>[`show-tag-names`](#show-tag-names)| Display tag names in the `tags` column, if defined.<br>Possible values: `false`, `true`.<br>Default value: `false`.<br>**Example**: `show-tag-names = true`| [↗](https://apps.axibase.com/chartlab/4afb9290/3/)
<a name="display-tags"></a>[`display-tags`](#display-tags)| Enumerate specific tags displayed in the `tags` column.<br>Possible values: `tag name`.<br>**Example**: `display-tags = mount_point`| [↗](https://apps.axibase.com/chartlab/220498ff/3/)
<a name="columns"></a>[`columns`](#columns)| Add multiple column keys by key.<br>**Example**: `columns = command`| [↗](https://apps.axibase.com/chartlab/d7c8ed94)
<a name="merge-columns"></a>[`merge-columns`](#merge-columns)| Group columns by key.<br>**Example**: `merge-columns = entity`| [↗](https://apps.axibase.com/chartlab/cd464c8e)
<a name="sort"></a>[`sort`](#sort)| Sort table rows by column or property value.<br>Specify descending (`DESC`) or ascending (`ASC`) order.<br>**Example**: `sort = memfree ASC`| [↗](https://apps.axibase.com/chartlab/4ec19a01)
<a name="transpose"></a>[`transpose`](#transpose)| Transpose table rows.<br>Possible values: `false`, `true`.<br>Default: `false`.<br>**Example**: `transpose = true`| [↗](https://apps.axibase.com/chartlab/fe7940e7)
<a name="replace-underscore"></a>[`replace-underscore`](#replace-underscore)| Replace underscores with whitespace in column names.<br>Possible values: `false`, `true`.<br>Default value: `false`.<br>**Example**: `replace-underscore = true`| [↗](https://apps.axibase.com/chartlab/47565e08)
<a name="capitalize"></a>[`capitalize`](#capitalize)| Capitalize header names.<br>Possible values: `false`, `true`.<br>Default value: `false`.<br>**Example**: `capitalize = false`| [↗](https://apps.axibase.com/chartlab/b04865b4)

### Style and Layout Settings

* The settings apply to the `[widget]` section.

Name | Description | &nbsp;
:--|:--|:--
<a name="class"></a>[`class`](#class)| Table class.<br>Possible settings: `terminal`.<br>**Example**: `class = terminal` | [↗](https://apps.axibase.com/chartlab/a535ad11)
<a name="responsive"></a>[`responsive`](#responsive)| Adjust font size based on widget dimensions.<br>Possible values: `false`, `true`.<br>Default value: `true`.<br>**Example**: `responsive = false`| [↗](https://apps.axibase.com/chartlab/c862e097)
<a name="font-scale"></a>[`font-scale`](#font-scale)| Ratio of font height to row height when `auto-height = true`.<br>Minimum row height is `10px`, maximum row height is `64px`.<br>Default: `0.5`.<br>**Example**: `font-scale = 0.7`| [↗](https://apps.axibase.com/chartlab/ed4d8748)
<a name="table-header-style"></a>[`table-header-style`](#table-header-style)| Table header CSS style.<br>Hide table header with `table-header-style = display: none`.<br>**Example**: `table-header-style = font: 24 px`| [↗](https://apps.axibase.com/chartlab/1a277cd8)
<a name="header-style"></a>[`header-style`](#header-style)| Widget header CSS style.<br>Hide widget header with `header-style = display: none`.<br>**Example**: `background-color: steelblue`| [↗](https://apps.axibase.com/chartlab/343efa22)
<a name="auto-height"></a>[`auto-height`](#auto-height)| Assign row height based on vertical space allocated to the widget and number of rows.<br>Possible values: `false`, `true`.<br>Default: `false`.<br>**Example**: `auto-height = true`| [↗](https://apps.axibase.com/chartlab/8cef1677)

:::tip

To increase font size for all table widgets in the portal, add the [global style](https://apps.axibase.com/chartlab/14318c01).

```javascript
script = $('<style>.axi-table-cell {font-size: 20px} </style>').appendTo('head')
```

:::

### Column Settings

* The settings apply to the `[column]` section.

Name | Description | &nbsp;
:--|:--|:--
<a name="key"></a>[`key`](#key)|**Optional** key name.<br>Use to sort by column name.<br>If the name of the key is a property from a server object, the value of the cell is the value of the property.<br>**Example**: `key = pid`| [↗](https://apps.axibase.com/chartlab/79cde58f)
<a name="tag"></a>[`tag`](#tag)|**Optional** tag name column.<br>Needed when an object received from the server contains property tags.<br>Value of the cell by default is equal to the value of the tag.<br>**Example**: `tag = file_system`|[↗](https://apps.axibase.com/chartlab/f9ddebdb/2/)
<a name="format"></a>[`format`](#format)|Cell value [format](../../syntax/format-settings.md).<br>**Examples**:<ul><li>`format = kilobytes`</li><li>`format= ####`</li></ul>|[↗](https://apps.axibase.com/chartlab/95bd95be/8/)
<a name="label"></a>[`label`](#label)| Name of column displayed in the column title.<br>Can be specified as JavaScript code.<br>**Example**: `label = Virtual`| [↗](https://apps.axibase.com/chartlab/95bd95be/8/)
<a name="tooltip"></a>[`tooltip`](#tooltip)|Column description, displayed upon title mouseover.<br>**Example**: `tooltip = Process CPU Usage`|[↗](https://apps.axibase.com/chartlab/95bd95be/9/)
<a name="style"></a>[`style`](#style)|Style assigned to the column.<br>Can be specified as JavaScript code.<br>**Examples**:<ul><li>`style = text-align: left`</li><li>`style = background: orange`</li><li>`style = max-width: 50%`</li></ul>|[↗](https://apps.axibase.com/chartlab/95bd95be/23/)
<a name="row-style"></a>[`row-style`](#row-style)|Style assigned to the entire row.<br>Can be specified as JavaScript code.<br>**Example**: `row-style = value > 1 ? 'background: orange' : null`|[↗](https://apps.axibase.com/chartlab/95bd95be/24/)
<a name="row-alert-style"></a>[`row-alert-style`](#row-alert-style)|Styles assigned to the whole row.<br>Can be specified as JavaScript code.<br>**Example**: `row-alert-style = background-color: orange`|[↗](https://apps.axibase.com/chartlab/95bd95be/12/)
<a name="display"></a>[`display`](#display)| Hide a column.<br>Default value is `true`.<br>**Example**: `display = false`| [↗](https://apps.axibase.com/chartlab/95bd95be/13/)
<a name="on-click"></a>[`on-click`](#on-click)|JavaScript code click event handler for each cell.<br>Supports `method` filter, which allows you to filter the rows in the table to the value of this cell.<br>**Examples**:<ul><li>`onclick = filter()`</li></ul>|[↗](https://apps.axibase.com/chartlab/95bd95be/15/)
<a name="icon"></a>[`icon`](#icon)|Name of the icon displayed in the cell.<br>Can be specified as JavaScript code.<br>**Example**: `icon = value > 1 ? 'exclamation-sign' : 'ok'`|[↗](https://apps.axibase.com/chartlab/95bd95be/25)
<a name="position"></a>[`position`](#position)|Position of the column relative to other columns in the table.<br>**Example**: `position = first`|[↗](https://apps.axibase.com/chartlab/d77c0677/6/)
<a name="series-value"></a>[`series-value`](#series-value) | JavaScript expression to calculate the value of a series.<br>Default value: none.<br>**Example**: `series-value = meta().metric.label` | [↗](https://trends.axibase.com/2d7e442b )
<a name="value"></a>[`value`](#value)|JavaScript expression to calculate cell value.<br>Default value: key or tag value.<br>**Example**: `value = row.openTime`|[↗](https://apps.axibase.com/chartlab/95bd95be/7/)

:::tip
Columns can be hidden or renamed using a short syntax `column-{key} = null` (hide) and `column-{key} = {name}` (rename). The following syntax options are equivalent.

```ls
column-time = null

[column]
  key = time
  display = false
```

```ls
column-entity = Server

[column]
  key = entity
  label = Server
```

### Column Order

Column order is determined by the order of `[column]` sections in the widget configuration.

Default widget columns have a pre-defined position, for example the `Severity` column in `Console` widget is positioned first by default.

To change the position of the default column, specify the column name explicitly in the widget configuration.

![](./images/column-order-example-1.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/3c57bf69)

`[column]` settings include the `position` setting to control the placement of the column regardless of the order in which `[column]` settings are defined in the widget. Possible values are `first`, `middle` and `last`.

![](./images/column-order-example-1.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/163a8733)
