# Time Chart

## Overview

The **Time Chart** displays series values at successive time intervals for one or more series. Data is loaded for a specified interval and updated as new samples are received.

```ls
[widget]
  type = chart

  [series]
    entity = nurswgvml007
    metric = cpu_busy
```

![](./images/time-chart.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/3146896d)

## Widget Settings

* The settings apply to the `[widget]` section
* [Shared](../shared/README.md) `[widget]` settings are inherited.

Name | Example | Description | &nbsp;
:--|:--|:--|:--
<a name="display-panels"></a>[`display-panels`](#display-panels)  |  `display-panels = true`  |  Display widget controls.<br>Possible values: `false`, `true`, `hover`.<br>Default value: `hover`. |  [↗](https://apps.axibase.com/chartlab/1a1bfdd3)
<a name="expand-panels"></a>[`expand-panels`](#expand-panels)  |  `expand-panels = compact`  |  Expand widget controls.<br>Allowed values: `all`, `compact`, `none`.  |  [↗](https://apps.axibase.com/chartlab/e9e8cd37)
<a name="periods"></a>[`periods`](#periods)  |  `periods = 20 minute, 4 hour`  |  Custom aggregation periods in widget controls.<br>Specified as the number of [time units](https://axibase.com/docs/atsd/api/data/series/time-unit.html).<br>Format: `count time_unit`.  |  [↗](https://apps.axibase.com/chartlab/eaf88286)
<a name="context-height"></a>[`context-height`](#context-height) | `context-height = 50` | Height of the [Context Chart](#time-chart-controls)<br>Default value: `0`.<br> | [↗](https://apps.axibase.com/chartlab/67d1027d)
<a name="markers"></a>[`markers`](#markers) | `markers = false` | Show series value markers.<br>Possible values: `false`, `true`.<br>Default value: `true`.| [↗](https://apps.axibase.com/chartlab/263a3ee8)
<a name="last-marker"></a>[`last-marker`](#last-marker) | `last-marker = false` | Show last series value marker.<br>Possible values: `false`, `true`. Default value: `true`. | [↗](https://apps.axibase.com/chartlab/5a54b7ce)
<a name="horizontal-grid"></a>[`horizontal-grid`](#horizontal-grid) | `horizontal-grid = false` | Show horizontal grid.<br>Possible values: `false`, `true`.<br>Default value: `true`. | [↗](https://apps.axibase.com/chartlab/a28cbb11)
<a name="vertical-grid"></a>[`vertical-grid`](#vertical-grid) | `vertical-grid = false` | Show vertical grid.<br>Possible values: `false`, `true`.<br>Default value: `true`. | [↗](https://apps.axibase.com/chartlab/50895463)
<a name="pointer-position"></a>[`pointer-position`](#pointer-position) | `pointer-position = left` | Location of final value pointer.<br>Possible values: `left`, `right`, `none`.<br>Default value: `right`.| [↗](https://apps.axibase.com/chartlab/33aa5216)
<a name="step-line"></a>[`step-line`](#step-line) | `step-line = true` | Display step line.<br>Possible values: `false`, `true`.<br>Default value: `false`. | [↗](https://apps.axibase.com/chartlab/024cbe4f)
<a name="auto-period"></a>[`auto-period`](#auto-period) | `auto-period = false` | Assign series aggregation period to the value of four time intervals.<br>Possible values: `false`, `true`.<br>Default value: `true`.| [↗](https://apps.axibase.com/chartlab/ff922a73)
<a name="disconnect-interval"></a>[`disconnect-interval`](#disconnect-interval) | `disconnect-interval = 10 minute` | Maximum time gap between samples specified as the number of [time units](https://axibase.com/docs/atsd/api/data/series/time-unit.html).<br>If the gap between samples exceeds the specified interval, data points are not connected.<br>Possible values:  `count time unit`. | [↗](https://apps.axibase.com/chartlab/2edca4d7)
<a name="disconnect-count"></a>[`disconnect-count`](#disconnect-count) | `disconnect-count = 50` | Maximum distance between samples specified as the number of periods.<br>If the gap between samples exceeds the defined value, data points are not connected.<br>If `disconnect-count = 1`, the interval is equal to the interval between samples.| [↗](https://apps.axibase.com/chartlab/2792adc4)
<a name="disconnect-value"></a>[`disconnect-value`](#disconnect-value)| `disconnect-value = 0` | Value applied to disconnected areas.| [↗](https://apps.axibase.com/chartlab/32f6fef5)
<a name="moving-average"></a>[`moving-average`](#moving-average) | `moving-average = true` | Moving average based on a sliding window which ends at the current time.<br>Possible values: `false`, `true`.<br>Default value: `false`.| [↗](https://apps.axibase.com/chartlab/10124798)
<a name="negative-style"></a>[`negative-style`](#negative-style) | `negative-style = fill: red` | CSS style applied to negative values in `column` or `column-stack` mode. | [↗](https://apps.axibase.com/chartlab/8dc77d01)
<a name="current-period-style"></a>[`current-period-style`](#current-period-style) | `current-period-style = fill-opacity: 0; stroke-width: 2; stroke-dasharray: 5, 2, 1, 2` | CSS styles applied to current period values in `column` and `column-stack` mode.| [↗](https://apps.axibase.com/chartlab/64ea74d4)
<a name="forecast-style"></a>[`forecast-style`](#forecast-style) | `forecast-style = stroke: magenta; opacity: 0.25` | CSS style applied to [forecasts](https://axibase.com/docs/atsd/forecasting/) in `column` and `column-stack` mode.| [↗](https://apps.axibase.com/chartlab/b3e87541)

### Value Axis Settings

Name | Example | Description | &nbsp;
:--|:--|:--|:--
<a name="auto-scale"></a>[`auto-scale`](#auto-scale) | `auto-scale = true` | Scale the value axis based on series values.<br>Possible values: `false`, `true`.<br>Default value: `false`. | [↗](https://apps.axibase.com/chartlab/4256fd76)
<a name="ticks"></a>[`ticks`](#ticks) | `ticks = 10` | Tick marks on the left axis.<br>Default value: `5`. | [↗](https://apps.axibase.com/chartlab/08a8bf45)
<a name="ticks-right"></a>[`ticks-right`](#ticks-right) | `ticks-right = 10` | Tick marks on the right axis.<br>Default value: `5`. | [↗](https://apps.axibase.com/chartlab/3972fb62)

### Time Axis Settings

Name | Example | Description | &nbsp;
:--|:--|:--|:--
<a name="ahead-time-span"></a>[`ahead-time-span`](#ahead-time-span) | `ahead-time-span = 80%` | Visualized time ahead of final series value.<br>Possible values: Percent value in `0.10` notation or `10%` notation.| [↗](https://apps.axibase.com/chartlab/c559d591)
<a name="rotate-ticks"></a>[`rotate-ticks`](#rotate-ticks) | `rotate-ticks = 0` | Rotate labels on the time axis by `n` degrees.<br>Possible values: between `0` (horizontal) and `90` (vertical), or `true` (horizontal).<br>Default value: `90` (vertical).| [↗](https://apps.axibase.com/chartlab/5b2621a8)
<a name="centralize-ticks"></a>[`centralize-ticks`](#centralize-ticks) | `centralize-ticks = true` | Center time and date markers over ticks.<br>Possible values: `false`, `true`.<br>Default value: `false`.| [↗](https://apps.axibase.com/chartlab/e100936c)
<a name="ticks-time"></a>[`ticks-time`](#ticks-time) | `ticks-time = 20` | Tick marks on the time axis.<br>Default value: `10`. | [↗](https://apps.axibase.com/chartlab/addb441e)
<a name="time-offset"></a>[`time-offset`](#time-offset) |`time-offset = 10 week` | Time series offset specified as the number of [time units](https://axibase.com/docs/atsd/api/data/series/time-unit.html).<br>`time-offset > 0`: Offset into the past.<br> `time-offset < 0`: Offset into the future.<br>Format: `count time_unit`.| [↗](https://apps.axibase.com/chartlab/23e8049e)
<a name="display-date"></a>[`display-date`](#display-date) | `display-date = true` | Display the time period captured by the **Time Chart**.<br>Possible values: `false`, `true`.<br>Default value: `false`.| [↗](https://apps.axibase.com/chartlab/37738a05)
<a name="retain-time-span"></a>[`retain-time-span`](#retain-time-span) | `retain-time-span = false` | Maintain widget `timespan` as new data is added.<br>Possible values: `false`, `true`<br>Default value: `true`.| [↗](https://apps.axibase.com/chartlab/48eed908)

## Series Settings

* The settings apply to the `[series]` section.
* [Shared](../shared/README.md#series-settings) `[series]` settings are inherited.

Name | Example | Description | &nbsp;
:--|:--|:--|:--
<a name="mode"></a>[`mode`](#mode) | `mode = column`| Chart mode.<br>Possible values `line` - Connect series data points with a line. `stack` - Visually stack series. `column` - Display series as columns. `range` - Display range of series values. `column-stack` - Visually stack series in column-form.<br>Default value: `line`.| [↗](https://apps.axibase.com/chartlab/267a5534)
<a name="fill-value"></a>[`fill-value`](#fill-value) | `fill-value = true`| Interpolate a series with irregularly spaced values.<br>Detailed values are filled using [`linear` interpolation](https://axibase.com/docs/atsd/api/data/series/aggregate.html#interpolation-functions).<br>Aggregated periods are filled with `previous` values.<br>Possible values: `false`, `true`<br>Default value: `true`.| [↗](https://apps.axibase.com/chartlab/033b40d5)
<a name="load-future-data"></a>[`load-future-data`](#load-future-data) | `load-future-data = true` | Load future series values.<br>Import forecasts generated by third-party tools such as [R Language](https://github.com/axibase/atsd-api-r/blob/master/README.md#atsd-r-package).<br>Possible values: `false`, `true`.<br>Default value: `false` | [↗](https://apps.axibase.com/chartlab/cf472245)
<a name="series-type"></a>[`series-type`](#series-type) | `series-type = s1` | Grouping parameter for `stack` mode.<br>Series of the same type are grouped.| [↗](https://apps.axibase.com/chartlab/2ad5b8ae)

## Threshold Settings

* The settings apply to the `[threshold]` section.
* Use `[threshold]` settings to define series thresholds:
  * Load the series and include `display = false` settings under `[widget]` settings.
  * Assign the series an `alias`.
  * In the `[threshold]` section, specify threshold value with `value = value('alias')` as seen in the **ChartLab** example below.

![](./images/threshold-settings-2.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/d32f63e0)

Name | Example | Description | &nbsp;
:--|:--|:--|:--
<a name="threshold-label"></a>[`label`](#threshold-label) | `label = threshold` | Threshold legend label.| [↗](https://apps.axibase.com/chartlab/6669e7a4)
<a name="threshold-color"></a>[`color`](#threshold-color) | `color = red` | Threshold color.| [↗](https://apps.axibase.com/chartlab/bf478ab6)
<a name="threshold-value"></a>[`value`](#threshold-value) | `value = 75`| Threshold value.| [↗](https://apps.axibase.com/chartlab/8bcd5a38)

## **Time Chart** Controls

* Modify selection interval and aggregation period on the fly.
* Add custom selection intervals and aggregation periods directly on the **Time Chart**.
* Apply various aggregations without reloading the portal.
* Change the chart mode: `line`, `column`, `range`, `stack`.
* View data in the appropriate format: hertz, joules, watts, bytes, percent, currency etc.
* Create custom metrics using custom formulas and aggregations.
* Modify alert rules directly in the portal.
* Instantly generate forecasts in the **Time Chart**.

![](./images/time-chart-controls.png)

1. **Title**: Click the title to expand the widget to fullscreen.
1. **Timespan**: Select one of the available timespans from the menu.
1. **Series Icon**: Toggle visibility of displayed series by clicking the icon to show or hide that series.
1. **Forecast Tools**: Display forecast and confidence intervals for series.
1. **Mode**: Select the display mode for the series.
1. **Aggregation**: Select aggregation method for the series.
1. **Aggregation Period**: Define the aggregation period for the series.
1. **Left Axis**: Scale the left axis manually by dragging. Double click to reset values to default.
1. **Right Axis**: Scale the right axis manually by dragging. Double click to reset values to default.
1. **Scale Options**: Auto-scale the value of axes in the **Time Chart**. Display the series in step-line format. Toggle value markers for the series.
1. **Load All Data**: Double click **Time Chart** surface to show all loaded data.
1. **Time Axis**: Scale the time axis manually by dragging. Double click to reset values to default.
1. **Context Chart**: Select a manual timespan by dragging context chart endpoints.

### Modifying **Time Chart** Controls

Add selection intervals and aggregation periods directly in **Time Chart** controls by double clicking the whitespace between the interval or period where a new interval needs to be added. An interval or period roughly half way between the two values is added on each double click.

![](./images/add-new-timespan-1.png)

To add a four-day (`4d`) aggregation period, double click between `1d` and `1w` on the aggregation period controls of the **Time Chart**.

![](./images/add-new-timespan-2.png)

To remove selection intervals and aggregation periods, drag and drop the interval or period off the **Time Chart** controls. In the example below, the one-week (`1w`) timespan is removed.

![](./images/add-new-timespan-3.png)

## Examples

### `time-offset` Setting

![](./images/time-offset-settings.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/ebd90c87)

### Dual Axis

![](./images/dual-axis-1.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/2deaef48)

### Stack Average

![](./images/stack-average-settings.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/2b8d550c)

### Fill Area

![](./images/fill-area.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/8bc482c9)

### `alert-expression` Example

![](./images/alert-expression-example.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/b3892525)

### Percentile

![](./images/percentile-statistics.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/fbf744aa)

### Forecast

![](./images/data-type-forecast.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/e2880896)

### `disconnect-interval` and `disconnect-value`

![](./images/interval-and-value.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/7101d5b9)

### `[threshold]` Settings

![](./images/threshold-settings-example.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/ec3cabf2)

### `value` Settings Example

![](./images/value-settings-example.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/e11254b7)

### `value` Statistic Example

![](./images/value-statistic-example.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/ada21b87)

### Message Overlay

Insert messages into the database as series, using series tags to encode message text. Add messages to a **Time Chart** with `mode=column` setting.

![](./images/message-overlay-1.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/e14cb99c)

### Elapsed Time

Overlay multiple intervals on the time axis with interval formatting.

![](./images/interval-format-settings.png)

[![](../../images/button.png)](https://apps.axibase.com/chartlab/8a35d47d)
