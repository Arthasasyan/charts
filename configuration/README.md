# Configuration

## Overview

Configuration settings specify the overall layout of a widget or group of widgets.

## Configuration Settings

* The settings apply to the `[configuration]` section of all widgets.

### General Settings

Name | Description | &nbsp;
:--|:--|:--
<a name="dialog-maximize"></a>[`dialog-maximize`](#dialog-maximize)|  Expand dialog window to the entire page.<br>Open dialog window by clicking the widget header.<br>Possible values: `false`, `true`.<br>Default: `true`.<br>**Example**: `dialog-maximize = true`.  |  [↗](https://apps.axibase.com/chartlab/8bc68a84)
<a name="scale"></a>[`scale`](#scale)| Chart scale.<br>Value must exceed `0.0`.<br>Default value: `1.0`.<br>**Example**: `scale = 0.8`.| [↗](https://apps.axibase.com/chartlab/1679114f)

### Layout Settings

Name | Description | &nbsp;
:--|:--|:--
<a name="height-units"></a>[`height-units`](#height-units) | When specified in the `[configuration]` section, `height-units` determines the number of rows in the portal.<br>When specified in the `[widget]` or `[group]` section `height-units` determines the number of rows the widget occupies.<br>Default value: `4`.<br>**Example**: `height-units = 2`.|[↗](https://apps.axibase.com/chartlab/645ea8fb)
<a name="width-units"></a>[`width-units`](#width-units)| When specified in the `[configuration]` section, `width-units` determines the number of columns in the portal.<br>When specified in the `[widget]` or `[group]` section `width-units` determines the number of columns the widget occupies.<br>Default value: `6`.<br>**Example**: `width-units = 2`.|[↗](https://apps.axibase.com/chartlab/d74e423d)
<a name="offset-left"></a>[`offset-left`](#offset-left)| Offset from the left page border, in pixels.<br>Default value: `0`.<br>**Example**: `offset-left = 50`.| [↗](https://apps.axibase.com/chartlab/8e901887)
<a name="offset-right"></a>[`offset-right`](#offset-right) | Offset from the right page border, in pixels.<br>Default value: `0`.<br>**Example**: `offset-right = 50`. | [↗](https://apps.axibase.com/chartlab/59feef54)
<a name="offset-top"></a>[`offset-top`](#offset-top)| Offset from the top page border, in pixels.<br>Default value: `0`.<br>**Example**: `offset-top = 50`. | [↗](https://apps.axibase.com/chartlab/706f24e5)
<a name="offset-bottom"></a>[`offset-bottom`](#offset-bottom)| Offset from the bottom page border, in pixels.<br>Default value: `0`.<br>**Example**:  `offset-bottom = 50`. | [↗](https://apps.axibase.com/chartlab/5e7b62aa)
<a name="widgets-per-row"></a>[`widgets-per-row`](#widgets-per-row)  | Maximum number of widgets per `[group]`.<br> Additional widgets are placed in a new row.<br>**Example**: `widgets-per-row = 2`.  |  [↗](https://apps.axibase.com/chartlab/90047c70) |