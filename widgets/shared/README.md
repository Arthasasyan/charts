# Shared Settings

## Overview

The **Shared Settings** are common settings supported by all widgets.

## Widget Settings

* The settings apply to the `[widget]` section.

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`type`](#type) | `type = chart`| Widget visualization type: [`chart`](../time-chart/README.md), [`gauge`](../gauge-chart/README.md), [`bar`](../bar-chart/README.md), [`histogram`](../histogram/README.md), [`box`](../box-chart/README.md), [`calendar`](../calendar-chart/README.md), [`treemap`](../treemap/README.md), [`pie`](../pie-chart/README.md), [`console`](../alert-console/README.md), [`property`](../property-table/README.md), [`text`](../text-widget/README.md), [`page`](../page-widget/README.md), [`graph`](../graph/README.md)| [↗](https://apps.axibase.com/chartlab/e926d483)
[`tooltip`](#tooltip) | `tooltip = Daily Averages` | Widget description displayed on title mouseover. | [↗](https://apps.axibase.com/chartlab/61c9771e)
[`header-style`](#header-style)| `header-style = color: red`| CSS style to change the header color or to hide it.| [↗](https://apps.axibase.com/chartlab/b4c45b71/2/)
[`colors`](#colors) | `colors = green, #ccc` | Comma separated list of colors applied to series shapes: lines, rectangles, or circles, depending on the widget type.<br>Possible values: [color names](https://en.wikipedia.org/wiki/Web_colors) or hex codes.<br>Default value: `steelblue, orange, green, purple`.| [↗](https://apps.axibase.com/chartlab/55dde7a7)
[`offset-left`](#offset) | `offset-left = 50` | Offset from the left page border, in pixels.<br>Default value: `0`. | [↗](https://apps.axibase.com/chartlab/720677c3)
[`offset-right`](#offset) | `offset-right = 50` | Offset from the right page border, in pixels.<br>Default value: `0`. | [↗](https://apps.axibase.com/chartlab/7c30a34b)
[`offset-top`](#offset) | `offset-top = 50` | Offset from the top page border, in pixels.<br>Default value: `0`. | [↗](https://apps.axibase.com/chartlab/fcbb484b)
[`offset-bottom`](#offset) | `offset-bottom = 50` | Offset from the bottom page border, in pixels.<br>Default value: `0`. | [↗](https://apps.axibase.com/chartlab/1baa3e3a)
[`scale`](#scale) | `scale = 0.8` | Chart scale.<br>Value must exceed `0.0`.<br>Default value: `1.0`.| [↗](https://apps.axibase.com/chartlab/1679114f)

### Data Loading

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`timespan`](#timespan) | `timespan = 6 hour` | Date interval specified as the number of [time units](https://axibase.com/docs/atsd/api/data/series/time-unit.html).<br>Format: `count time_unit`.<br>Default value: `1 hour`.| [↗](https://apps.axibase.com/chartlab/f08405c6)
[`series-limit`](#series-limit) | `series-limit = 10` | Maximum number of series retrieved from the database.<br>Default value: `1000`| [↗](https://apps.axibase.com/chartlab/af34dc29)
[`limit`](#limit) | `limit = 10` | Maximum number of samples returned for each returned series.<br>Default value: `0` (not limited).|[↗](https://apps.axibase.com/chartlab/13549b9c/2/)<br>[↗](https://apps.axibase.com/chartlab/2604d710)
[`cache`](#cache) | `cache = true` | Query last values from the cache table for fast response.<br>Default value: `false`| [↗](https://apps.axibase.com/chartlab/032bcfcc)
[`refresh-interval`](#refresh-interval) | `refresh-interval = 5 minute` | Interval to refresh data specified as the number of [time units](https://axibase.com/docs/atsd/api/data/series/time-unit.html).<br>Format: `count time_unit`.<br>Default value: `5 seconds`. | [↗](https://apps.axibase.com/chartlab/da03b8a5/24/)
[`retry-refresh-interval`](#retry-refresh-interval) | `retry-refresh-interval = 5 minute`| Interval to skip requesting data for the given series if if the previous request received empty response, specified as the number of [time units](https://axibase.com/docs/atsd/api/data/series/time-unit.html).<br>Format: `count time_unit`. | [↗](https://apps.axibase.com/chartlab/bf0babfc)
[`error-refresh-interval`](#error-refresh-interval) | `error-refresh-interval = 30 minute`| Interval to skip requesting data for the given series if the previous request failed, specified as the number of [time units](https://axibase.com/docs/atsd/api/data/series/time-unit.html).<br>Format: `count time_unit`. | [↗](https://apps.axibase.com/chartlab/9f482e52)

### Legend

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`legend-position`](#legend-position) | `legend-position = left` | Legend location.<br>Possible values: `hidden`, `top`, `right`, `bottom`, `left`<br>Default value: `hidden`.<br>Combine values to define corners.| [↗](https://apps.axibase.com/chartlab/b962dd26)
[`label-format`](#format-labels)| `label-format = entity` | Series label pattern consisting of literal text and [placeholders](../../syntax/label-formatting.md).| [↗](https://apps.axibase.com/chartlab/f2bed31b)

### Axis

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`axis-title`](#axis-title) | `axis-title = CPU Usage in %`| Vertical text displayed along the left axis.| [↗](https://apps.axibase.com/chartlab/d8adfe73)
[`axis-title-right`](#axis-title) | `axis-title-right = Free Memory`| Vertical text displayed along the right axis.| [↗](https://apps.axibase.com/chartlab/d8adfe73)
[`day-format`](#day-format) | `day-format = %y/%m/%d`| [Day format](../../syntax/format-settings.md#day-format) applied to time axis.| [↗](https://apps.axibase.com/chartlab/40dafe6b/2/)
[`min-range`](#min-range) | `min-range = 0`| Left axis minimum range.<br>If loaded data exceeds `min-range` value, widget is scaled to show true minimum range.| [↗](https://apps.axibase.com/chartlab/d9eeeda5)
[`max-range`](#max-range) | `max-range = 100`| Left axis maximum range.<br>If loaded data exceeds `max-range` value, widget is scaled to show true maximum range.| [↗](https://apps.axibase.com/chartlab/74052e3e)
[`min-range-right`](#min-range-right) | `min-range-right = 0`| Right axis minimum range.<br>If loaded data exceeds `min-range-right` value, widget is scaled to show true minimum range.| [↗](https://apps.axibase.com/chartlab/a5d7f10b)
[`max-range-right`](#max-range-right) | `max-range-right = 100`| Right axis maximum range.<br>If loaded data exceeds `max-range-right` value, widget is scaled to show true maximum range.| [↗](https://apps.axibase.com/chartlab/5f1445c6)
[`max-range-force`](#max-range-force) | `max-range-force = 100` | Left axis forced minimum and maximum range.<br>If loaded data exceeds `max-range-force`, widget is not scaled to show true maximum range. | [↗](https://apps.axibase.com/chartlab/fa0b58a7)
[`min-range-force`](#min-range-force) | `min-range-force = 0` | Left axis forced minimum and maximum range.<br>If loaded data exceeds `min-range-force`, widget is not scaled to show true minimum range. | [↗](https://apps.axibase.com/chartlab/fa0b58a7)
[`min-range-right-force`](#min-range-right-force) | `min-range-right-force = 0` | Right axis forced minimum range.<br>If loaded data exceeds `min-range-right-force`, widget is not scaled to show true maximum range. | [↗](https://apps.axibase.com/chartlab/ac40afc3)
[`max-range-right-force`](#max-range-right-force) | `max-range-right-force = 100` | Right axis forced maximum range.<br>If loaded data exceeds `max-range-right-force`, widget is not scaled to show true maximum range. | [↗](https://apps.axibase.com/chartlab/ac40afc3)

## Series Settings

* The settings apply to the `[series]` section.

### Series Selection

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`metric`](#metric) | `metric = cpu_busy` | Metric name.<br>When requesting data from a relational database specify both `table` and `attribute` as an alternative. | [↗](https://apps.axibase.com/chartlab/4e4994ea)
[`table`](#table) | `table = KLZ_CPU`| Table in the relational database from which to retrieve numeric values.<br>Alternative to `metric` setting.<br>Both `table` and `attribute` must be defined.| [↗](https://apps.axibase.com/chartlab/35fde2bf)
[`attribute`](#attribute) | `attribute = Current_Average` | Column name in a relational database table. The column must be of numeric data type.  | [↗](https://apps.axibase.com/chartlab/35fde2bf)
[`data-type`](#data-type) | `data-type = forecast` | Series data type.<br>Possible values: `history`, `forecast`, `forecast_deviation`, `lower_confidence`, `upper_confidence`.| [↗](https://apps.axibase.com/chartlab/08625792)
[`forecast-name`](#forecast-name) | `forecast-name = hw5` | Forecast name.<br>If no forecast name is defined, [default series forecast](https://axibase.com/docs/atsd/forecasting/#persistence-settings) is loaded.| [↗](https://apps.axibase.com/chartlab/3e5fa03c)

### Entity Filter

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`entity`](#entity) | `entity = nurswgvml007`<br>`entity = nurswgvml00*`| Entity name.<br>Supports `?` and `*` [wildcards](../../syntax/wildcards.md).| [↗](https://apps.axibase.com/chartlab/d65bdce1)
[`entities`](#entities)| `entities = nurswgvml007, nurswgvml008`| Select multiple entities with one setting.<br>If both `entity` and `entities` are specified, `entity` takes precedence.<br>Supports `?` and `*` [wildcards](../../syntax/wildcards.md)| [↗](https://apps.axibase.com/chartlab/e1d30997/2/)
[`entity-group`](#entity-group) | `entity-group = nmon-sub-group` | [Entity group](https://axibase.com/docs/atsd/configuration/entity_groups.html) name. | [↗](https://apps.axibase.com/chartlab/5e951ce2)
[`entity-expression`](#entity-expression) | `entity-expression = tags.app LIKE '*a*'` | Server-side [entity filter](https://axibase.com/docs/atsd/api/data/filter-entity.html#entityexpression-syntax) to select series for matching entities by name, tags, and fields.| [↗](https://apps.axibase.com/chartlab/ffc97c51)

### Tag Filter

To select series with specific tags, add a `[tags]` section or define a condition using the `tag-expression` setting.

```ls
[series]
  metric = disk_used
  entity = nurswgvml007
  [tags]
    mount_point = /tmp
    fstype = tmpfs
```

To match multiple values for the same tag, separate the values with a comma. Escape commas if necessary using backslash.

```ls
[tags]
  tag_name = tag_value1, tag\,value
```

To match multiple tag values, use `?` and `*` wildcards:

```ls
[tags]
  tag_name = *val*
```

If the tag name contains an equals sign `=`, a comma`,`, or reserved names such as setting names, enclose the tag name in double quotes to avoid collisions:

```ls
[tags]
  "type" = sensor
  "tag\=name" = tag\,value
```

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`tag-expression`](#tag-expression)| `tag-expression = tags.make LIKE 'AU*'`| Server-side [tag filter](https://axibase.com/docs/atsd/api/data/series/query.html#tag-expression) to select series for matching tags.| [↗](https://apps.axibase.com/chartlab/135a3458)
[`exact-match`](#exact-match) | `exact-match = true` | Ignore series with tags other than those [specified](https://axibase.com/docs/atsd/api/data/series/query.html#tag-filter) in the `[tags]` section.<br>Default value: `false` | [↗](https://apps.axibase.com/chartlab/dada4561/2/)

### Series Style

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`color`](#color) | `color = orange` | Series color.<br>Possible values: [color name](https://en.wikipedia.org/wiki/Web_colors) or hex code. | [↗](https://apps.axibase.com/chartlab/18bbef10)
[`label`](#label) | `label = CPU Busy - nurswgvml007` | Series label displayed in the legend. Overrides `label-format`. | [↗](https://apps.axibase.com/chartlab/dad7c267)
[`style`](#style) | `style = stroke-width: 4`<br>`style = stroke-dasharray: 5 1 2` | CSS style applied to the series shape.| [↗](https://apps.axibase.com/chartlab/fb6d13d9)<br>[↗](https://apps.axibase.com/chartlab/6d91d52f) [↗](https://apps.axibase.com/chartlab/5e47cfbe)
[`tooltip`](#tooltip) | `tooltip = NURSWGVML007` | Tooltips displayed on mouseover. | [↗](https://apps.axibase.com/chartlab/1687516c)
[`axis`](#axis) | `axis = right` | Series axis placement.<br>Possible values: `left`, `right`<br>Default value: `left`| [↗](https://apps.axibase.com/chartlab/da03b8a5/20/)
[`format`](#format)| `format = kilobytes` | Format series values with a [measurement unit](../../syntax/format-settings.md).| [↗](https://apps.axibase.com/chartlab/c957cf22)
[`display`](#display) | `display = value > top(3)`<br>`display = false` | Hide series based on boolean value or [expression](https://axibase.com/docs/atsd/administration/metric-persistence-filter.html#expression-syntax).| [↗](https://apps.axibase.com/chartlab/fbbab68b)<br>[↗](https://apps.axibase.com/chartlab/628cd2b0)<br>
[`enabled`](#enabled) | `enabled = false`<br>`enabled = max('1 day') > 10` | Toggle series visibility based on boolean value or [expression](https://axibase.com/docs/atsd/administration/metric-persistence-filter.html#expression-syntax).<br>Series legend remains visible when `false`. | [↗](https://apps.axibase.com/chartlab/63c18977)
[`alert-expression`](#alert-expression)| `alert-expression = value < 95` | Boolean expression to apply conditional CSS style to series shapes.<br>The CSS style must be specified in the `alert-style` setting.<br>The `value` field refers to the series value. | [↗](https://apps.axibase.com/chartlab/e389a1ab)
[`alert-style`](#alert-style) | `alert-style = fill: red; stroke: red`| CSS style applied to the series shape if `alert-expression` returns `true`.| [↗](https://apps.axibase.com/chartlab/ddd854be)
[`audio-alert`](#audio-alert) | `audio-alert = /portal/resource/alarm.ogg`| Play an [audio file](../../configuration/audio-alerts.md) when `alert-expression` evaluates to `true`.| [↗](https://apps.axibase.com/chartlab/59a834f3/2/)

### Transformation

#### Rate

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`rate`](#rate) | `rate = 15 second` | Compute the difference between consecutive samples per unit of time, or [rate period](https://axibase.com/docs/atsd/api/data/series/rate.html#rate-period).<br>Format: `count time_unit` or `auto`.<br>Default value: `auto` (None)| [↗](https://apps.axibase.com/chartlab/d2daeb40)
[`rate-counter`](#rate-counter) | `rate-counter = true`| Ignore differences between consecutive samples.<br>Default value: `false`| [↗](https://apps.axibase.com/chartlab/d91e674f)

> See also [Rate](https://axibase.com/docs/atsd/api/data/series/rate.html) transformation in REST API.

#### Aggregation

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`statistics`](#statistics) | `statistic = avg`| Aggregation statistic functions.<br>Refer to [Aggregators](../../configuration/aggregators.md) for possible values.| [↗](https://apps.axibase.com/chartlab/0143f4e7)
[`period`](#period) | `period = 15 minute`| [Aggregator](https://axibase.com/docs/atsd/api/data/series/aggregate.html#aggregate-processor) period.<br>Possible values: `count` + [time unit](https://axibase.com/docs/atsd/api/data/series/time-unit.html)| [↗](https://apps.axibase.com/chartlab/661181a3)
[`align`](#align) | `align = END_TIME` | [Alignment](https://axibase.com/docs/atsd/api/data/series/aggregate.html#period) of the period start or end time.<br>Possible values: `CALENDAR`, `START_TIME`, `END_TIME`, `FIRST_VALUE_TIME`.<br>Default value: `CALENDAR`.| [↗](https://apps.axibase.com/chartlab/e2b5bc91)
[`interpolate`](#interpolate) | `interpolate = LINEAR` | Interpolate missing aggregation periods.<br>Possible values: `NONE`, `LINEAR`, `PREVIOUS`, `NEXT`, `VALUE(n)`, where `n` is the numerical value to be used to fill missing samples.<br>Default value: `NONE` | [↗](https://apps.axibase.com/chartlab/7af6f848)
[`interpolate-extend`](#interpolate-extend)| `interpolate-extend = true` | Interpolate leading and trailing periods with `NEXT` or `PREVIOUS` value.| [↗](https://apps.axibase.com/chartlab/4a3b8f7a)

> See also [Aggregation](https://axibase.com/docs/atsd/api/data/series/aggregate.html) transformation in REST API.

#### Interpolation

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`interpolate-function`](#interpolate-function) | `interpolate-function = linear` | Interpolation function applied to detailed samples.<br>Possible values: `NONE`, `LINEAR`, `PREVIOUS`, `NEXT`, `VALUE(n)`, where `n` is the numerical value to be used to fill missing samples.<br>Default value: `NONE`| [↗](https://apps.axibase.com/chartlab/6221d836)
[`interpolate-period`](#interpolate-period) | `interpolate-period = 1 minute` | Define the period for interpolated values.<br>Possible values:<br>`count` + [time unit](https://axibase.com/docs/atsd/api/data/series/time-unit.html) | [↗](https://apps.axibase.com/chartlab/6221d836)
[`interpolate-boundary`](#interpolate-boundary) | `interpolate-boundary = outer` | [Interpolation](https://axibase.com/docs/atsd/api/data/series/interpolate.html#boundary) for leading and trailing values.<br>Possible values:<br>`inner`: Data outside of the selection interval is not loaded by the database.<br>`outer`: One value before and one value after the selection interval is loaded by the database to interpolate leading and trailing values.<br>Default value: `inner`| [↗](https://apps.axibase.com/chartlab/5713cdf9)
[`interpolation-fill`](#interpolation-fill) | `interpolate-fill = true` | Interpolate values outside of the selection interval.<br>Possible values: `true`, `false`, `count` of values to fill.<br>Default value: `false`| [↗](https://apps.axibase.com/chartlab/9361ea19)

> See also [Interpolation](https://axibase.com/docs/atsd/api/data/series/interpolate.html) transformation in REST API.

#### Grouping

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`merge-fields`](#merge-fields) | `merge-fields = mount_point`<br>`merge-fields = entity`|Group series based on merge field.<br>Only applies in `multiple-series` mode.<br>By default, series which use [wildcard](../../syntax/wildcards.md), `entities`, `entityGroup` settings or comma-separated tag values are treated as multiple series.<br>Possible values:<br>`entity`: Combine all series with the same entity.<br>`tag-name`: Combine all series with tag defined by `tag-name`. | [↗](https://apps.axibase.com/chartlab/3d45a84c)
[`group-statistic`](#group-statistic) | `group-statistic = sum` | Group statistic function assigned to the series.<br>Refer to [Aggregators](../../configuration/aggregators.md) for possible values.| [↗](https://apps.axibase.com/chartlab/fb67609c)
[`group-period`](#group-period) | `group period = 1 month` | Group period over which to calculate [group statistics](https://axibase.com/docs/atsd/api/data/series/group.html#group-processor).<br>Possible values:<br>`auto`, `count` + [time unit](https://axibase.com/docs/atsd/api/data/series/time-unit.html)<br>Default value: `auto` (`15 minutes`)| [↗](https://apps.axibase.com/chartlab/2ee1bace)
[`group-first`](#group-first) | `group-first = false` | The sequence of aggregation and grouping.<br>If set to `true`, grouping is performed before aggregation.| [↗](https://apps.axibase.com/chartlab/732de421)
[`group-interpolate`](#group-interpolation) | `group-interpolate = LINEAR` | Interpolate grouped values.<br>Possible values: `LINEAR`, `PREVIOUS`, `VALUE` | [↗](https://apps.axibase.com/chartlab/f0a36dac)
[`group-interpolate-extend`](#group-interpolate-extend) | `group-interpolate-extend = true` | Fill missing leading and trailing periods with `NEXT` or `PREVIOUS` values.| [↗](https://apps.axibase.com/chartlab/f0a36dac)

> See also [Grouping](https://axibase.com/docs/atsd/api/data/series/group.html) transformation in REST API.

#### Downsampling

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`downsample`](#downsample) | `downsample = true` | Enable [downsampling](https://axibase.com/docs/atsd/api/data/series/downsample.html#downsampling).<br>Boolean expression.<br>Default value: `false`.| [↗](https://apps.axibase.com/chartlab/5d8aba18)
[`downsample-gap`](#downsample-gap) | `downsample-gap = 10 minute` | Frequency of repeated values by defining [`downsample-gap`](https://axibase.com/docs/atsd/api/data/series/downsample.html#parameters) as a time interval.<br>A larger gap value decreases the occurrence of repeated values.<br>Possible values: <br>`auto`, `count` + [time unit](https://axibase.com/docs/atsd/api/data/series/time-unit.html)<br>Default value: `auto` (`10 minutes`)| [↗](https://apps.axibase.com/chartlab/d8d2d8d0)
[`downsample-ratio`](#downsample-ratio) | `downsample-ratio = 1.1` | Downsample [ratio](https://axibase.com/docs/atsd/api/data/series/downsample.html#ratio-check).| [↗](https://apps.axibase.com/chartlab/3945b3cb)
[`downsample-algorithm`](#downsample-algorithm) | `downsample-algorithm = interpolate` | [Downsample algorithm](https://axibase.com/docs/atsd/api/data/series/downsample.html#algorithm) used in calculation.<br>Possible values: `DETAIL`, `INTERPOLATE`.<br>Default value: `DETAIL`.| [↗](https://apps.axibase.com/chartlab/196c2069)
[`downsample-difference`](#downsample-difference) | `downsample-difference = 4` |Deviation between consecutive values which ATSD considers equivalent.<br>Consolidate samples with minor deviations when downsampling. | [↗](https://apps.axibase.com/chartlab/6d27e45f)

> See also [Downsampling](https://axibase.com/docs/atsd/api/data/series/downsample.html) transformation in REST API.

#### Smoothing

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`smooth`](#smooth) | `smooth = AVG` | [Averaging](https://axibase.com/docs/atsd/api/data/series/smooth.html) function applied to window samples.<br>Possible values: `AVG`, `EMA`, `WAVG`, `WTAVG` | [↗](https://apps.axibase.com/chartlab/3734bd35/4)
[`smooth-factor`](#smooth-range) | `smooth-factor = 0.5` | [`EMA`](https://axibase.com/docs/atsd/api/data/series/smooth.html#exponential-moving-average) function weight parameter. Possible values: between `0` and `1`. | [↗](https://apps.axibase.com/chartlab/3734bd35/4)
[`smooth-range`](#smooth-range) | `smooth-range = 60000` | Alternative [`EMA`](https://axibase.com/docs/atsd/api/data/series/smooth.html#exponential-moving-average) function weight parameter. | [↗](https://apps.axibase.com/chartlab/3734bd35/4)
[`smooth-count`](#smooth-count) | `smooth-count = 50` | Window size.<br>A larger window performs greater smoothing. | [↗](https://apps.axibase.com/chartlab/3734bd35/4)
[`smooth-interval`](#smooth-interval) | `smooth-interval = 15 minute` | Window duration interval. | [↗](https://apps.axibase.com/chartlab/3734bd35/4)
[`smooth-minimum-count`](#smooth-minimum-count) | `smooth-minimum-count = 10` | [Minimum number](https://axibase.com/docs/atsd/api/data/series/smooth.html#fields) of samples in a window required to apply the smoothing function.<br>Default value: `1` | [↗](https://apps.axibase.com/chartlab/3734bd35/4)
[`smooth-incomplete-value`](#smooth-incomplete-value) | `smooth-incomplete-value = NaN` | Sample value returned when downsampling window is not full. | [↗](https://apps.axibase.com/chartlab/3734bd35/4)

> See also [Smoothing](https://axibase.com/docs/atsd/api/data/series/smooth.html) transformation in REST API.

### Derived Value Settings

Specify `value` setting to create calculated series derived from raw series using arithmetic expressions in JavaScript syntax. The expression returns a number or `null`.

Name | Example | Description | &nbsp;
:--|:--|:--|:--
[`replace-value`](#replace-value) | `replace-value = value*2`| Modify or filter series values.<br>Supported fields: `value`.| [↗](https://apps.axibase.com/chartlab/1e4dccf0/2/)
[`alias`](#alias) | `alias = s1` | Unique series name to pass data to other series. | [↗](https://apps.axibase.com/chartlab/e0623f81)
[`value`](#value) | `value = max('s1')`| Define series value.<br>Retrieve the value of the underlying series identified by alias.| [↗](https://apps.axibase.com/chartlab/6428aa9c)<br>[↗](https://apps.axibase.com/chartlab/a39c16f4)
