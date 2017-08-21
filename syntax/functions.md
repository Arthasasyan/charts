# <a name=header></a> Functions
This page contains descriptions of recently implemented functions.

## Overview


| Name | Arguments | Return | Description | Scope | API Request |
|------|-----------|--------|-------------|-------|-------------|
| [getTags()](#getTags) | metric <br> tagName <br> minInsertDate <br> maxInsertDate <br> url <br> queryParams | `Array<string>` | get series of `metric` filtered by `entity`, `minInsertDate` and `maxInsertDate` and return sorted array of unique values of tag with name `tagName` | preprocessor | [/api/v1/metrics/{metric}/series](https://github.com/axibase/atsd/blob/master/api/meta/metric/series.md) |
| [getSeries()](#getSeries)| metric <br> entity <br> minInsertDate <br> maxInsertDate <br> url <br> queryParams | `Array<object>` | return series of metric filtered by `entity`, `minInsertDate` and `maxInsertDate` | preprocessor |  [/api/v1/metrics/{metric}/series](https://github.com/axibase/atsd/blob/master/api/meta/metric/series.md)  |
| [getMetrics()](#getMetrics) | entity <br> expression <br> tags <br> url <br> queryParams | `Array<string>` | return names of metrics collected for `entity` filtered by `expression` | preprocessor | [/api/v1/entities/{entity}/metrics](https://github.com/axibase/atsd/blob/master/api/meta/entity/metrics.md) |
| [getEntities()](#getEntities) | group <br> expression <br> tags <br> url <br> queryParams | `Array<string>`  | return names of entities contained in entity-group filtered by `expression` | preprocessor | [/api/v1/entity-groups/{group}/entities](https://github.com/axibase/atsd/blob/master/api/meta/entity-group/get-entities.md) |
| [range()](#range) | start <br> end <br> step <br> format | `Array<number|string>` | generate array of numbers from `start` to `end` with `step` formatted with [format](https://axibase.com/products/axibase-time-series-database/visualization/widgets/configuring-the-widgets/format-settings/) | preprocessor | does not use network |
| [csv name = ...](#csv_inline) |  | `Array<object>` | parse CSV-like text into array of objects | preprocessor | does not use network |
| [csv name from ...](#csv_from)| url | `Array<object>` | load CSV file located at the `url` and parse it into array of objects | preprocessor |  `url`  |
| [csv.values()](#csv_values) | column_name | `Array<string>` | get sorted unique values of the `column_name` column | preprocessor | does not use network |
| [list.escape()](#list_escape) |  | `Array<string>` | escape commas in every element of array | preprocessor | does not use network |
| [global.escape()](#global_escape) | string | `string` | escape special characters in `string` with `\` | global | does not use network |
| [previous()](#previous) | alias <br> offset | `number` | get value of the previous point with `offset` | value-expression | does not use network |
| [movavg()](#movavg) | alias <br> count <br> minCount | `number` | compute moving average for `count` previous point if there at least `minCount` points | value-expression | does not use network |
| [meta()](#meta) | alias | `object` | get metadata object for series with `alias` | value-expression | does not use network |
| [entityTag()](#entityTag) | alias <br> tagName | `number` | get value of the entity tag `tagName` from metadata object for series with `alias` | value-expression | does not use network |
| [metricTag()](#metricTag) | alias <br> tagName | `number` | get value of the entity tag `tagName` from metadata object for series with `alias` | value-expression | does not use network |
| [requestMetricsSeriesValues()](#requestMetricsSeriesValues) | fieldPath <br> callback <br> metric <br> unique <br>  params | `Array<string>` | get series descriptors and retrieve `fieldPath` filed from each, apply `callback` to field values | dropdown | [/api/v1/metrics/{metric}/series](https://github.com/axibase/atsd/blob/master/api/meta/metric/series.md) |
| [requestEntitiesMetricsValues()](#requestEntitiesMetricsValues) | fieldPath <br> callback <br> entity <br> unique <br> params | `Array<string>` | get metrics descriptors and retrieve `fieldPath` filed from each, apply `callback` to field values | dropdown | [/api/v1/entities/{entity}/metrics](https://github.com/axibase/atsd/blob/master/api/meta/entity/metrics.md) |
| [requestPropertiesValues()](#requestPropertiesValues) | fieldPath <br> callback <br> entity <br> propertyType <br> unique <br> postBody | `Array<string>` | get entity or property descriptors and retrieve `fieldPath` filed from each, apply `callback` to field values | dropdown | [/api/v1/properties/query](https://github.com/axibase/atsd/blob/master/api/data/properties/query.md) |
| [requestMetricsSeriesOptions()](#requestMetricsSeriesOptions) | valueFieldPath <br> textFieldPath <br> callback <br> metric <br> unique <br> params | `Array<object>` | get series descriptors and retrieve `valueFieldPath` and `textFieldPath` to set option's value and text or apply `callback` to loaded descriptors | dropdown | [/api/v1/metrics/{metric}/series](https://github.com/axibase/atsd/blob/master/api/meta/metric/series.md) |
| [requestEntitiesMetricsOptions()](#requestEntitiesMetricsOptions) | valueFieldPath <br> textFieldPath <br> callback <br> entity <br> unique <br> params | `Array<object>` | get metric descriptors and retrieve `valueFieldPath` and `textFieldPath` to set option's value and text or apply `callback` to loaded descriptors | dropdown | [/api/v1/entities/{entity}/metrics](https://github.com/axibase/atsd/blob/master/api/meta/entity/metrics.md) |
| [requestPropertiesOptions()](#requestPropertiesOptions) | valueFieldPath <br> textFieldPath <br> callback <br> entity <br> propertyType <br> unique <br> postBody | `Array<object>` | get entity or property descriptors and retrieve `valueFieldPath` and `textFieldPath` to set option's value and text or apply `callback` to loaded descriptors | dropdown | [/api/v1/properties/query](https://github.com/axibase/atsd/blob/master/api/data/properties/query.md) |

<!-- ************************************ getTags() ************************************ -->
## [⇧](#header) <a name="getTags"></a> getTags()

### Description
Makes a synchronous request to the `{url}api/v1/metrics/{metric}/series?entity={entity}&minInsertDate={minInsertDate}&maxInsertDate={maxInsertDate}`. Receive series descriptor objects and retrieve unique values of `tagName` tag from each series descriptor. Retrived values are then sorted. This function can be used at the stage of preprocessing in the `var` expression. The returned array has `list.escape()` function, which escapes commas in every element.

[More information about API request](https://github.com/axibase/atsd/blob/master/api/meta/metric/series.md)

### Return value
`Array<string>` - unique sorted values of the specified `tagName` series tag.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| metric | required | string | `metric` path parameter |
| tagName | required | string | tag which values will be retrieved from series descriptors |
| entity | optional | string | `entity` query parameter |
| minInsertDate | optional | string | `minInsertDate` query parameter ([syntax](https://github.com/axibase/atsd/blob/master/end-time-syntax.md)) |
| maxInsertDate | optional | string | `maxInsertDate` query parameter ([syntax](https://github.com/axibase/atsd/blob/master/end-time-syntax.md)) |
| url | optional | string | protocol, host and path to which `/api/v1` path will be added |
| queryParams | optional | object | object with parameter names as keys and it's values as values, which will be transformed to query parameters string |

### Examples

#### Get values of `mount_point` tag in series for metric `disk_used` and entity `nurswgvml007` received today.

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa)

##### Usage

```
var mount_points = getTags("disk_used", "mount_point", "nurswgvml006", "current_day")
```

##### Sent request

```
/api/v1/metrics/disk_used/series?tag=mount_point&entity=nurswgvml006&minInsertDate=current_day
```

##### Result

 ``` json
 ["/", "/media/datadrive", "/mnt/u113452"]
 ```

#### <a name=requestParametersArg></a> Get values of `mount_point` tag in series for metric `disk_used` and entity `nurswgvml007` and send server-specific query parameter `cache` ignoring other parameters

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/2)

##### Usage

```
var mount_points = getTags("disk_used", "mount_point", "nurswgvml007", null, null, null, {cache: true})
```

##### Sent Request

```
/api/v1/metrics/disk_used/series?cache=true&tag=mount_point&entity=nurswgvml007
```

##### Result

``` json
["/", "/media/datadrive", "/mnt/u113452"]
```

<!-- ************************************ getSeries() ************************************ -->

## [⇧](#header) <a name="getSeries"></a> getSeries()

### Description
Makes a synchronous request to the `{url}api/v1/metrics/{metric}/series?entity={entity}&minInsertDate={minInsertDate}&maxInsertDate={maxInsertDate}`. Receive series descriptor objects and return it. This function can be used at the stage of preprocessing in the `var` expression.

[More information about API request](https://github.com/axibase/atsd/blob/master/api/meta/metric/series.md)

### Return value
`Array<object>` - received series descriptors.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| metric | required | string | `metric` path parameter |
| entity | optional | string | `entity` query parameter |
| minInsertDate | optional | string | `minInsertDate` query parameter ([syntax](https://github.com/axibase/atsd/blob/master/end-time-syntax.md)) |
| maxInsertDate | optional | string | `maxInsertDate` query parameter ([syntax](https://github.com/axibase/atsd/blob/master/end-time-syntax.md)) |
| url | optional | string | protocol, host and path to which `/api/v1` path will be added |
| queryParams | optional | object | object with parameter names as keys and it's values as values, which will be transformed to query parameters string |

### Examples

[Look at the example for `queryParams` argument in the `getTags()` section.](#requestParametersArg)

#### Get series for metric `disk_used` and entity `nurswgvml007`.

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/3)

##### Usage

```
var seriesDescriptors = getSeries("disk_used", "nurswgvml007")
```

##### Sent request

```
/api/v1/metrics/disk_used/series?entity=nurswgvml007
```

##### Result

 ``` json
[
    {
        "metric":"disk_used",
        "entity":"nurswgvml007",
        "tags":{
            "file_system":"/dev/mapper/vg_nurswgvml007-lv_root",
            "mount_point":"/"
        },
        "lastInsertDate":"2017-08-15T15:30:25.000Z"
    },
    {
        "metric":"disk_used",
        "entity":"nurswgvml007",
        "tags":{
            "file_system":"10.102.0.2:/home/store/share",
            "mount_point":"/mnt/share"
        },
        "lastInsertDate":"2015-12-25T14:09:49.000Z"
    },
    {
        "metric":"disk_used",
        "entity":"nurswgvml007",
        "tags":{
            "file_system":"//u113452.your-backup.de/backup",
            "mount_point":"/mnt/u113452"
        },
        "lastInsertDate":"2017-06-21T13:26:00.000Z"
    }
]
 ```


<!-- ************************************ getMetrics() ************************************ -->

## [⇧](#header) <a name="getMetrics"></a> getMetrics()

### Description
Makes a synchronous request to the `{url}api/v1/entities/{entity}/metrics?expression={expression}&tags={tags}`. Receive metric descriptor objects and return `name` field. This function can be used at the stage of preprocessing in the `var` expression. The returned array has `list.escape()` function, which escapes commas in every element.

[More information about API request](https://github.com/axibase/atsd/blob/master/api/meta/entity/metrics.md)

### Return value
`Array<string>` - retrieved metrics names.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| entity | required | string | `entity` path parameter |
| expression | optional | string | `expression` query parameter ([syntax](https://github.com/axibase/atsd/blob/master/api/meta/expression.md)) |
| tags | optional | string | `tags` request parameter |
| url | optional | string | protocol, host and path to which `/api/v1` path will be added |
| queryParams | optional | object | object with parameter names as keys and it's values as values, which will be transformed to query parameters string |

### Examples

[Look at the example for `queryParams` argument in the `getTags()` section.](#requestParametersArg)

#### Get metrics for entity `nurswgvml007` which contain "cpu" and "user" substrings.

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/4)

##### Usage

```
var metrics = getMetrics("nurswgvml007", "name LIKE '*cpu*user*'")
```

##### Sent request

```
/api/v1/entities/nurswgvml007/metrics?expression=name%20LIKE%20%27*cpu*user*%27
```

##### Result

 ``` json
["cpu_user","nmon.cpu.user%","nmon.cpu_total.user%"]
 ```


<!-- ************************************ getEntities() ************************************ -->

## [⇧](#header) <a name="getEntities"></a> getEntities()

### Description
Makes a synchronous request to the `{url}api/v1/entity-groups/{group}/entities?expression={expression}&tags={tags}`. Receive entity descriptor objects and return `name` field. This function can be used at the stage of preprocessing in the `var` expression. The returned array has `list.escape()` function, which escapes commas in every element.

[More information about API request](https://github.com/axibase/atsd/blob/master/api/meta/entity-group/get-entities.md)

### Return value
`Array<string>` - retrieved entities names.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| group | required | string | `group` path parameter |
| expression | optional | string | `expression` query parameter ([syntax](https://github.com/axibase/atsd/blob/master/api/meta/expression.md)) |
| tags | optional | string | `tags` request parameter |
| url | optional | string | protocol, host and path to which `/api/v1` path will be added |
| queryParams | optional | object | object with parameter names as keys and it's values as values, which will be transformed to query parameters string |

### Examples

[Look at the example for `queryParams` argument in the `getTags()` section.](#requestParametersArg)

#### Get entities contained in entity-group `docker-hosts` which names are started with `nur` substring.

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/5/)

##### Usage

```
var entities = getEntities("docker-hosts", "name LIKE 'nur*'")
```

##### Sent request

```
/api/v1/entity-groups/docker-hosts/entities?expression=name%20LIKE%20%27nur*%27
```

##### Result

 ``` json
["nurswghbs001"]
 ```


<!-- ************************************ range() ************************************ -->

## [⇧](#header) <a name="range"></a> range()

### Description
Generate array of numbers from `start` to `end` with `step` formatted with `format`. The default step equals 1. If start > end then numbers are generated in descending order.

### Return value
`Array<number|string>` - generated (optionally formatted) numbers.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| start | required | number | first number in list |
| end | required | number | last number is list |
| step | optional | number | offset betwen adjacent numbers |
| format | optional | string | formatter name ([available formats](https://axibase.com/products/axibase-time-series-database/visualization/widgets/configuring-the-widgets/format-settings)) |

### Examples

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/6/)

#### Get sequental numbers from 1 to 10

##### Usage

```
range(1,10)
```

##### Result

```
1,2,3,4,5,6,7,8,9,10
```

#### Get numbers from 1 to 10 with step 2

##### Usage

```
range(1,10,2)
```

##### Result

```
1,3,5,7,9
```

#### Get numbers from 10 to 1 with step 1

##### Usage

```
range(10,1)
```

##### Result

```
10,9,8,7,6,5,4,3,2,1
```

#### Get numbers from 10 to 1 with step 2

##### Usage

```
range(10,1,2)
```

##### Result

```
10,8,6,4,2
```

#### Format sequental numbers from 1 to 10 with percent

##### Usage

```
range(1,10,'percent')
```

##### Result

```
1%,2%,3%,4%,5%,6%,7%,8%,9%,10%
```

#### Get numbers from 1 to 10 with step 2 and format with percent

##### Usage

```
range(1,10,2,'percent')
```

##### Result

```
1%,3%,5%,7%,9%
```

#### Format sequental numbers from 1 to 10 as minutes

##### Usage

```
range(1,10,1,'intervalFormat("%M:%S")(value*1000)')
```

##### Result

```
00:01,00:02,00:03,00:04,00:05,00:06,00:07,00:08,00:09,00:10
```

#### Format sequental numbers from 1 to 12 with padding left zero

##### Usage

```
range(1, 12, "d3.format('02d')(value)")
```

##### Result

```
01,02,03,04,05,06,07,08,09,10,11,12
```



<!-- ************************************ csv inline() ************************************ -->

## [⇧](#header) <a name="csv_inline"></a> CSV inline text mode

### Description
Parse CSV-like text placed between `csv` and `endcsv` keywords. Limitation and features that applied:
 - There can be empty lines and spaces.
 - To escape spaces double-quotes(`"`) should be used.
 - Value should not contain double-quotes(`"`).
 - Multi-line orws are not supported.
 - Delimiter is comma (`,`)

Generated array has `.value(column_name)` method to get unique sorted values of some column.

### Syntax

```
csv name = header1, header2 ...
cell11, cell12 ...
cell21, cell22 ...
...
endcsv
```

### Return value
`Array<object>` - Array of rows represented as objects with headers as keys and cells as corresponding values.

### Examples

#### Create array of objects from tabular structure using `csv`

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/8/)

In the following example we write table in CSV-like format. There are two columns: `name` of the country and `value2006` - value in the year 2006. We want to find how much different from 2006 year the current value is. So we write the following csv:

```
  csv countries =
    name, value2006
    Brazil, 13.2
    Croatia, 4.9
    "Micronesia, Federated States of", 100
    Georgia, 48.2
    Tonga, 40.8
    Honduras, 38
    Liechtenstein, 5.9
    "Congo, Dem. Rep. of the (Kinshasa)",44.2
  endcsv

  country = @{countries.values('name').escape()}
```

This CSV will be transformed into the following array:

 ``` json
[
    {
        "name":"Brazil",
        "value2006":"13.2"
    },
    {
        "name":"Croatia",
        "value2006":"4.9"
    },
    {
        "name":"Micronesia, Federated States of",
        "value2006":"100"
    },
    {
        "name":"Georgia",
        "value2006":"48.2"
    },
    {
        "name":"Tonga",
        "value2006":"40.8"
    },
    {
        "name":"Honduras",
        "value2006":"38"
    },
    {
        "name":"Liechtenstein",
        "value2006":"5.9"
    },
    {
        "name":"Congo, Dem. Rep. of the (Kinshasa)",
        "value2006":"44.2"
    }
]
 ```

Then we iterate over created array and set value and entity based on retrieved country `name` and `value2006`.

```
for country in countries
    [series]
      replace-value = value - @{country.value2006}
      [tags]
        country = @{country.name.replace(",", "\\,")}
endfor
```



<!-- ************************************ csv from ************************************ -->

## [⇧](#header) <a name="csv_from"></a> CSV from mode

### Description
Parse CSV file located at the `url`. Limitation and features that applied to the text:
 - There can be empty lines and spaces.
 - To escape spaces double-quotes(`"`) should be used.
 - Value should not contain double-quotes(`"`).
 - Multi-line orws are not supported.
 - Delimiter is comma (`,`)

Generated array has `.value(column_name)` method to get unique sorted values of some column.

### Syntax

```
csv name = from `{url}`
```

### Return value
`Array<object>` - Array of rows represented as objects with headers as keys and cells as corresponding values.

### Examples

#### Create array of objects from CSV file

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/9/)
In the following example we want to find how much different from 2006 year the current value is.

We load CSV from https://raw.githubusercontent.com/axibase/atsd-use-cases/master/USVisaRefusal/Resources/visa-refusal.csv

Here are first rows of the file:

```
country,2006,2007,2008,2009,2010,2011,2012,2013,2014,2015,2016
Brazil,13.2,9.6,5.5,7,5.2,3.8,3.2,3.5,3.2,5.36,16.7
Croatia,4.9,5.1,5.1,5.3,5.3,6.3,4.4,5.9,6.1,5.29,6.78
"Micronesia, Federated States of",100,0,50,100,0,33.3,50,100,80,85.71,25
Georgia,48.2,55.4,46.6,49.7,43.6,40.2,31.8,38.3,48.2,50.58,62.82
Tonga,40.8,45.4,48.7,47.8,42.8,46.5,41.5,42.1,25.4,28.09,31.58
Honduras,38,37.7,33.6,29.2,29.2,27.6,29.8,37,36.8,39.73,42.76
Liechtenstein,5.9,6.7,0,12.5,5.9,0,0,10,11.1,0,0
```

Below is the setting to load and parse this file:

```
csv rows from https://raw.githubusercontent.com/axibase/atsd-use-cases/master/USVisaRefusal/Resources/visa-refusal.csv
```

Parsed array will be the following:

 ``` json
[
    {
        "2006":"13.2",
        "2007":"9.6",
        "2008":"5.5",
        "2009":"7",
        "2010":"5.2",
        "2011":"3.8",
        "2012":"3.2",
        "2013":"3.5",
        "2014":"3.2",
        "2015":"5.36",
        "2016":"16.7",
        "country":"Brazil"
    },
    {
        "2006":"4.9",
        "2007":"5.1",
        "2008":"5.1",
        "2009":"5.3",
        "2010":"5.3",
        "2011":"6.3",
        "2012":"4.4",
        "2013":"5.9",
        "2014":"6.1",
        "2015":"5.29",
        "2016":"6.78",
        "country":"Croatia"
        ...
    },
 ```

Then we iterate over created array and set value and entity based on retrieved country `name` and value or year `2006`.

```
  for row in rows
    [series]
      replace-value = value - @{row[2006]}
    [tags]
      country = @{row.country.replace(",", "\\,")}
  endfor
endfor
```


<!-- ************************************ csv.values() ************************************ -->

## [⇧](#header) <a name="csv_values"></a> csv.values()

### Description
Arrays generated from `csv` have `.values()` method. This function returns sorted array of unique values in the column `column_name`.

Generated array has `.escape()` method which escapes commas in each element.

### Syntax

```
csv_name.values(column_name)
```

### Return value
`Array<string>` - Array of unique values in the column `column_name`.

### Examples

#### Get escaped values of csv column

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/10/)
In this example we want to get a list of escaped country names.

We write the following csv:

``` csv
  csv countries =
    name, value2006
    Brazil, 13.2
    Croatia, 4.9
    "Micronesia, Federated States of", 100
    Georgia, 48.2
    Tonga, 40.8
    Honduras, 38
    Liechtenstein, 5.9
    "Congo, Dem. Rep. of the (Kinshasa)",44.2
  endcsv

  country = @{countries.values('name').escape()}
```

This CSV will be transformed into the following array:

 ``` json
[
    {
        "name":"Brazil",
        "value2006":"13.2"
    },
    {
        "name":"Croatia",
        "value2006":"4.9"
    },
    {
        "name":"Micronesia, Federated States of",
        "value2006":"100"
    },
    {
        "name":"Georgia",
        "value2006":"48.2"
    },
    {
        "name":"Tonga",
        "value2006":"40.8"
    },
    {
        "name":"Honduras",
        "value2006":"38"
    },
    {
        "name":"Liechtenstein",
        "value2006":"5.9"
    },
    {
        "name":"Congo, Dem. Rep. of the (Kinshasa)",
        "value2006":"44.2"
    }
]
 ```

Then retrieve values of the column `name`:

```
var names = countries.values('name')
```

Returnes values are the following

``` json
["Brazil","Congo, Dem. Rep. of the (Kinshasa)","Croatia","Georgia","Honduras","Liechtenstein","Micronesia, Federated States of","Tonga"]
```

Then we iterate over values and set the country tag.

```
  for country_name in names
    [series]
    [tags]
      country = @{country_name.replace(',', '\\,')}
  endfor
```


<!-- ************************************ list.escape() ************************************ -->

## [⇧](#header) <a name="list_escape"></a> list.escape()

### Description
Escapes commas in each value in the array of strings. `.escape()` method is available in arrays generated from `list` keyword, `var` expression, and `csv.values()` method.

### Syntax

```
list_name.escape()
```

### Return value
`Array<string>` - joint by comma elements of array with escaped commas. (If type of argument is not string it returned as is)

### Examples

In the following examples we want to get a list of escaped country names. Countries names are generated from the `list`, `var` and `csv.values()`

#### Apply `.escape()` to array generated from `list`

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/11/)

##### Usage

```
  list countries =
    Brazil,
    Croatia,
    Micronesia\, Federated States of,
    Georgia,
    Tonga,
    Honduras,
    Liechtenstein,
    Congo\, Dem. Rep. of the (Kinshasa)
  endlist

  country = @{countries.escape()}
```

##### Result

```
["Brazil","Croatia","Micronesia\\, Federated States of","Georgia","Tonga","Honduras","Liechtenstein","Congo\\, Dem. Rep. of the (Kinshasa)"]
```

#### Apply `.escape()` to array created in `var` expression

[ChartLab](https://apps.axibase.com/chartlab/df616dfa/12/)

##### Usage

```
var countries = getTags('state.visa-refusal-rate', 'country', 'travel.state.gov')

country = @{countries.escape()}
```

##### Result
Part of result:

```
[... "Comoros","Congo\\, Dem. Rep. of the (Kinshasa)","Congo\\, Rep. of the (Brazzaville)","Costa Rica","Cote d'Ivoire" ...]
```

#### Apply `.escape()` to array retrived by `csv.values()`

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/7/)

##### Usage

```
csv countries =
  name, value2006
  Brazil, 13.2
  Croatia, 4.9
  "Micronesia, Federated States of", 100
  Georgia, 48.2
  Tonga, 40.8
  Honduras, 38
  Liechtenstein, 5.9
  "Congo, Dem. Rep. of the (Kinshasa)",44.2
endcsv

country = @{countries.values('name').escape()}
```

##### Result

```
["Brazil","Congo\\, Dem. Rep. of the (Kinshasa)","Croatia","Georgia","Honduras","Liechtenstein","Micronesia\\, Federated States of","Tonga"]
```



<!-- ************************************ global.escape() ************************************ -->

## [⇧](#header) <a name="global_escape"></a> global.escape()

### Description

Escape special characters in the string. Special characters are `-`, `/`, `\`, `^`, `$`, `*`, `+`, `?`, `.`, `(`, `)`, `|`,  `[`, `]`, `{`, `}`. Usually it is used to escape symbols in regular expression.
This function is stored in `window` object as other [string utils](https://axibase.com/products/axibase-time-series-database/visualization/widgets/label-formatting/), while `list.escape()` belongs to it's array.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| string | required | string | string in which symbols should be escaped |

### Syntax

```
escape()
```

### Return value

`string` - string with escaped special characters.

### Examples

#### Create regular expression using escape() to filter metric names

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/13/)

##### Usage
Assume we someway get part of metric name `immigrant-visa`. To escape special symbols use

```
var metricNamePart = 'immigrant-visa'
var escapedPart = escape(metricNamePart)
```

Then create regular expression to filter metric names:

```
m.match('state\..*' + escapedPart)
```

##### Result

```
"immigrant\-visa"
```






<!-- ************************************ previous() ************************************ -->

## [⇧](#header) <a name="previous"></a> previous()

### Description

Get the value in the previous point of the series with `alias`. Relative to current point index can be controlled by the `offset` argument. This function can be executed in `value-expression`.

### Return value
`number` - value of the previous point.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| alias | optional | string | alias of the series, which previous value should be retrieved |
| offset | optional | number | the index of the previous point relatively to current point, default is 1 |

### Examples

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/21)

#### Show copy of the seres shifted to the one point

#### Usage

```
value = previous('raw')
```

#### Result

![](images/previous_one.png)

#### Show copy of the seres shifted to the two points

#### Usage

```
value = previous('raw', 2)
```

#### Result

![](images/previous_two.png)


#### Show percentage difference of the last and last - 1 points

#### Usage

```
value = 1 - previous('raw') / value('raw')
```

#### Result

![](images/previous_diff_one.png)


#### Show percentage difference of the last and last - 1 points

#### Usage

```
value = 1 - previous('raw', 2) / value('raw')
```

#### Result

![](images/previous_diff_two.png)





<!-- ************************************ movavg() ************************************ -->

## [⇧](#header) <a name="movavg"></a> movavg()

### Description

Calculates moving average on `count` previous points on the series with `alias`. Average is calculated if at least `minCount` previous points are available.  This function can be executed in `value-expression`.

### Return value
`number` - value of the previous point.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| alias | optional | string | alias of the series, to which movavg should be applied |
| count | required | number | number of points for which movavg is will be calculated |
| minCount | optional | number | minimal number of points, for which movavg will be calculated, default is `count` |

### Examples

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/22/)

#### Caluculate movavg only when there is enough points for calculation

##### Usage

```
value = movavg('raw', 30)
```

##### Result

![](images/movavg_without_minCount.png)

#### Caluculate movavg whether there is enough points for calculation or not

##### Usage

```
value = movavg('raw', 30, 0)
```

##### Result

![](images/movavg_with_minCount.png)




<!-- ************************************ meta() ************************************ -->

## [⇧](#header) <a name="meta"></a> meta()

### Description

Return metadata loaded for series with `alias`. The `[series]` `add-meta` setting should be equal to true. This function can be executed in `value-expression`. Current limitation of the function: it should be used with `value(alias)` in one expression.

### Return value
`object` - metadata loaded to series.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| alias | optional | string | alias of the series, which metadata is returned |

### Examples

#### Fraction of the maxValue

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/23/)

##### Usage

```
value = value('raw') / meta('raw').metric.maxValue
```

##### Result

![](images/meta_maxValue.png)




<!-- ************************************ entityTag() ************************************ -->

## [⇧](#header) <a name="entityTag"></a> entityTag()

### Description

Return tag with `tagName` from entity metadata loaded for series with `alias`. The `[series]` `add-meta` setting should be equal to true. This function can be executed in `value-expression`.

### Return value
`number` - value of specified entity tag.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| alias | optional | string | alias of the series, which metadata is returned |
| tagName | required | string | name of tag which is retrieved from `meta.entity.tags` |

### Examples

#### Set size to 'cpu_count' entity tag

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/24/)

##### Usage

```
size = entityTag('cpu_count')
```

##### Result
![](images/entityTag.png)





<!-- ************************************ metricTag() ************************************ -->

## [⇧](#header) <a name="metricTag"></a> metricTag()

### Description

Return tag with `tagName` from metric metadata loaded for series with `alias`. The `[series]` `add-meta` setting should be equal to true. This function can be executed in `value-expression`.

### Return value
`string` - value of specified metric tag.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| alias | optional | string | alias of the series, which metadata is returned |
| tagName | required | string | name of tag which is retrieved from `meta.metric.tags` |

### Examples

#### Set threshold to 'threshold_value' metric tag

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/25/)

##### Usage

```
value = metricTag('raw', 'threshold_value')
alert-expression = value() > metricTag('threshold_value')
```

##### Result

![](images/metricTag.png)



<!-- ************************************ VALUES FUNCTIONS ************************************ -->



<!-- ************************************ requestMetricsSeriesValues() ************************************ -->

## [⇧](#header) <a name="requestMetricsSeriesValues"></a> requestMetricsSeriesValues()

### Description
Makes an asynchronous request to the `api/v1/metrics/{metric}/series`. Get array of series descriptors and then retrive value of the field on the `fieldPath`. The `callback` can be applied to the retrieved values or initial series descriptors. If setting specified in dropdown's `change-field` is not set in config, this function set it to the value of the first option.

[More information about API request](https://github.com/axibase/atsd/blob/master/api/meta/metric/series.md)

### Return value
`Array<string>` - values to fill the dropdown, retrived from series descriptors.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| fieldPath | optional | string | dot-separated path to the field, which value will be retrieved [expanded description](#valuesFieldPath) |
| callback | optional | function | function to process series descriptors or retrieved values [expanded description](#valuesCallback) |
| metric | optional | string | metrics, for which series are loaded. If not specified, `metric` from the `[widget]` is used |
| unique | optional | boolean | specify should retrieved values be unique and sorted, default is true |
| params | optional | string/object | string or key-value object representing request parameters |

### Examples

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/14/)

To fill dropdown with values of `mount_point` tag we can use the function as follows. The `fieldPath` `"tags.mount_point"` means we want for each descriptor to step into `tags` then get the `mount_point` field.

```
  [dropdown]
    options = javascript: requestMetricsSeriesValues("tags.mount_point")
    change-field = series.tags.mount_point
```

Below is content of the dropdown.

![](images/requestMetricsSeriesValues:fieldPath:tags.png)




<!-- ************************************ requestEntitiesMetricsValues() ************************************ -->

## [⇧](#header) <a name="requestEntitiesMetricsValues"></a> requestEntitiesMetricsValues()

### Description
Makes an asynchronous request to the `api/v1/entities/{entity}/metrics`. Get array of metrics descriptors and then retrive value of the field on the `fieldPath`. The `callback` can be applied to the retrieved values or initial metrics descriptors. If setting specified in dropdown's `change-field` is not set in config, this function set it to the value of the first option.

[More information about API request](https://github.com/axibase/atsd/blob/master/api/meta/entity/metrics.md)

### Return value
`Array<string>` - values to fill the dropdown, retrived from metrics' descriptors.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| fieldPath | optional | string | dot-separated path to the field, which value will be retrieved [expanded description](#valuesFieldPath) |
| callback | optional | function | function to process series descriptors or retrieved values [expanded description](#valuesCallback) |
| entity | optional | string | entity, for which metric descriptors are loaded. If not specified, `entity` from the `[widget]` is used |
| unique | optional | boolean | specify should retrieved values be unique and sorted, default is true |
| params | optional | string/object | string or key-value object representing request parameters |

### Examples

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/16/)

To fill dropdown with names of metrics, collected for the entity we can use the function as follows.

```
  [dropdown]
    options = javascript: requestEntitiesMetricsValues("name")
    change-field = series.metric
```

Below is content of the dropdown.

![](images/requestEntitiesMetricsValues.png)



<!-- ************************************ requestPropertiesValues() ************************************ -->

## [⇧](#header) <a name="requestPropertiesValues"></a> requestPropertiesValues()

### Description
Makes an asynchronous POST request to the `/api/v1/properties/query`. Get array of entities or properties descriptors and then retrieve value of the field on the `fieldPath`. The `callback` can be applied to the retrieved values or initial entities or properties descriptors. If setting specified in dropdown's `change-field` is not set in config, this function set it to the value of the first option.

[More information about API request](https://github.com/axibase/atsd/blob/master/api/data/properties/query.md)

### Return value
`Array<string>` - values to fill the dropdown, retrived from properties descriptors.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| fieldPath | optional | string | dot-separated path to the field, which value will be retrieved [expanded description](#valuesFieldPath) |
| callback | optional | function | function to process series descriptors or retrieved values [expanded description](#valuesCallback) |
| entity | optional | string | Array<string> | entity/entities, for which properties descriptors are loaded. If not specified, `entities` or `entity` from the `[widget]` is used |
| propertyType | optional | string | string | type of loaded properties, default is "$entity_tags" |
| unique | optional | boolean | specify should retrieved values be unique and sorted, default is true |
| postBody | optional/object | body of [Data API properties query](https://github.com/axibase/atsd/blob/master/api/data/properties/query.md) |

### Examples

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/17/)

To fill dropdown with ids of `network` properties we can use the function as follows.

```
  [dropdown]
    options = javascript: requestPropertiesValues("key.id", null, null, "network")
    change-field = property.keys.id
```

Below is content of the dropdown.

![](images/requestPropertiesValues.png)





## <a name="dropValuesFuncArgs"></a> Dropdown's Values Functions' Arguments Description

### <a name=valuesFieldPath></a> FieldPath _(optional, type: string)_

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/14/)

`fieldPath` is the dot-separated path to field in series descriptor object. If not specified series descriptors objects are returned. If specified, the field found by `fieldPath` is returned.


To fill dropdown with names of entities for which the metric is collected we can use the function as follows. The `fieldPath` `"entity"` means we want to get entity field from each descriptor.

```
[dropdown]
  options = javascript: requestMetricsSeriesValues("entity")
  change-field = series.entity
```

Below is content of the dropdown.

![](images/requestMetricsSeriesValues:fieldPath:entity.png)


To fill dropdown with values of `mount_point` tag we can use the function as follows. The `fieldPath` `"tags.mount_point"` means we want for each descriptor to step into `tags` then get the `mount_point` field.

```
  [dropdown]
    options = javascript: requestMetricsSeriesValues("tags.mount_point")
    change-field = series.tags.mount_point
```

Below is content of the dropdown.

![](images/requestMetricsSeriesValues:fieldPath:tags.png)


#### <a name=valuesCallback></a> Callback _(optional, type:function)_

`callback` can be used for manual processing of the series descriptors or additional processing of retrieved field values. If `fieldPath` is specified, the string values of some field are given as argument to the callback. Otherwise series descriptors array wold be the argument.

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/15/)

To fill dropdown with values of `mount_point` tag of series, which entity name is starting with `nur` we can use the function as below. Note, that series can be filtered by entity using `expression` queryParameter.

```
  [dropdown]
    change-field = series.tags.mount_point

    options = javascript: requestMetricsSeriesValues(null,
    options = function (series) {
    options =   var mountPoints = [];
    options =   series.forEach(function(s){
    options =     if(s.entity.indexOf("nur") === 0 && mountPoints.indexOf(s.tags.mount_point) < 0) {
    options =  		mountPoints.push(s.tags.mount_point);
    options =  	  }
    options =  	});
    options =  	return mountPoints.sort();
    options = })
```

Below is content of the dropdown.

![](images/requestMetricsSeriesValues:callback_without_fieldPath.png)

To fill dropdown with entity tag value we need to make two requests: get entities' names from series descriptors and then request entity tags for that entities.

```
[dropdown]
   change-field = series.entity

   options = javascript: requestMetricsSeriesValues("entity",
   options = function (entities) {
   options =   return requestPropertiesOptions("entity", "tags.app", null, entities);
   options = })
```

Below is content of the dropdown.

![](images/requestMetricsSeriesValues:callback_with_fieldPath.png)




<!-- ************************************ OPTIONS FUNCTIONS ************************************ -->


<!-- ************************************ requestMetricsSeriesOptions() ************************************ -->

## [⇧](#header) <a name="requestMetricsSeriesOptions"></a> requestMetricsSeriesOptions()

### Description
Makes an asynchronous GET request to the `api/v1/metrics/{metric}/series`. Get array of series descriptors and then create array of options using `valueFieldPath` as option value and `textFieldPath` as option text. The `callback` can be applied to the initial series descriptors. If setting specified in dropdown's `change-field` is not set in config, this function set it to the value of the first option.

[More information about API request](https://github.com/axibase/atsd/blob/master/api/meta/metric/series.md)

### Return value
`Array<{value: string, text: string}>` - options, generated from series descriptors fields'.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| valueFieldPath | optional | string | dot-separated path to the field, which value will be used as option's value |
| textFieldPath | optional | string/Array<string> | dot-separated path (or array of such pathes) to the field, which value will be used as option's text [expanded description](#optionsFieldPath) |
| callback | optional | function | function to process series descriptors, should return array of options [expanded description](#optionsCallback) |
| metric | optional | string | metric, for which series are loaded. If not specified, `metric` from the `[widget]` is used |
| unique | optional | boolean | applied to raw series descriptors, so is *useless* |
| params | optional | string/object | string or key-value object representing request parameters |

### Examples

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/18/)

To fill dropdown with options, in which value is the value of `iucr` tag and text is `description` tag we can use the function as follows.

```
[dropdown]
  options = javascript: requestMetricsSeriesOptions("tags.iucr", "tags.description")
  change-field = series.tags.iucr
```

Below is content of the dropdown.

![](images/requestMetricsSeriesOptions.png)




<!-- ************************************ requestEntitiesMetricsOptions() ************************************ -->

## [⇧](#header) <a name="requestEntitiesMetricsOptions"></a> requestEntitiesMetricsOptions()

### Description
Makes an asynchronous GET request to the `api/v1/entities/{entity}/metrics`. Get array of metrics descriptors and then create array of options using `valueFieldPath` as option value and `textFieldPath` as option text. The `callback` can be applied to the initial series descriptors. If setting specified in dropdown's `change-field` is not set in config, this function set it to the value of the first option.

[More information about API request](https://github.com/axibase/atsd/blob/master/api/meta/entity/metrics.md)

### Return value
`Array<{value: string, text: string}>` - options, generated from metrics descriptors fields'.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| valueFieldPath | optional | string | dot-separated path to the field, which value will be used as option's value |
| textFieldPath | optional | string/Array<string> | dot-separated path (or array of such pathes) to the field, which value will be used as option's text [expanded description](#optionsFieldPath) |
| callback | optional | function | function to process series descriptors, should return array of options [expanded description](#optionsCallback) |
| entity | optional | string | entity, for which metrics descriptors are loaded. If not specified, `entity` from the `[widget]` is used |
| unique | optional | boolean | applied to raw series descriptors, so is *useless* |
| params | optional | string/object | string or key-value object representing request parameters |

### Examples

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/19/)

To fill dropdown with options, in which value is the value of `iucr` tag and text is `description` tag we can use the function as follows.

```
  [dropdown]
    options = javascript: requestEntitiesMetricsOptions("name", "tags.description", null, null, null, {tags:"*",limit:15})
    change-field = metric
```

Below is content of the dropdown.

![](images/requestEntitiesMetricsOptions.png)




<!-- ************************************ requestPropertiesValues() ************************************ -->

## [⇧](#header) <a name="requestPropertiesOptions"></a> requestPropertiesOptions()

### Description
Makes an asynchronous POST request to the `/api/v1/properties/query`. Get array of entities or properties descriptors and then retrieve value of the field on the `fieldPath`. The `callback` can be applied to the initial entities or properties descriptors and should return array of options. If setting specified in dropdown's `change-field` is not set in config, this function set it to the value of the first option.

[More information about API request](https://github.com/axibase/atsd/blob/master/api/data/properties/query.md)

### Return value
`Array<string>` - options, generated from properties or entities descriptors' fields.

### Arguments

| Name | Necessity | Type | Description |
|------|-----------|------|-------------|
| valueFieldPath | optional | string | dot-separated path to the field, which value will be used as option's value |
| textFieldPath | optional | string/Array<string> | dot-separated path (or array of such pathes) to the field, which value will be used as option's text [expanded description](#optionsFieldPath) |
| callback | optional | function | function to process series descriptors, should return array of options [expanded description](#optionsCallback) |
| entity | optional | string/Array<string> | entity/entities, for which properties descriptors are loaded. If not specified, `entities` or `entity` from the `[widget]` is used |
| propertyType | optional | string | string | type of loaded properties, default is "$entity_tags" |
| unique | optional | boolean | applied to raw series descriptors, so is *useless* |
| postBody | optional | object | body of [Data API properties query](https://github.com/axibase/atsd/blob/master/api/data/properties/query.md) |

### Examples

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/20/)

To fill dropdown with options in which value is the `entity` and text is tag `app` we can use the function as follows..

```
  [dropdown]
    options = javascript: requestPropertiesOptions("entity", "tags.app", null, ["nurswgvml006", "nurswgvml007", "nurswgvml010", "nurswgvml301", "nurswgvml502"], "$entity_tags")
    change-field = entity

```

Below is content of the dropdown.

![](images/requestPropertiesOptions.png)



<!-- ************************************ OPTIONS ARGUMENTS ************************************ -->




## <a name="dropOptionsFuncArgs"></a> Dropdown's Options Functions' Arguments Description

### <a name=optionsFieldPath></a> TextFieldPath _(optional, type: string|Array<string>)_

[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/14/)

`textFieldPath` is the dot-separated path to field in series descriptor object or array of such paths. If it is an array then second and further elements are used as text if search on previous path failed. If `textFieldPath` is not specified or search on all path failed the value is used as text.


To fill dropdown with options in which value is retrieved from `name` field of metric descriptor and text from tag `description` we can use `textFieldPath` as string.

```
  [dropdown]
    options = javascript: requestEntitiesMetricsOptions('name', 'tags.description', null, null, null, {tags:'*',limit:15})
    change-field = metric
```

Below is content of the dropdown.

![](images/options:fieldPath:string.png)


To fill dropdown with options in which value is retrieved from `name` field of metric descriptor and text from tag `description` or tag `documentation`, if descriptor has no value for tag `description`, we can use `textFieldPath` as array.

```
  [dropdown]
    options = javascript: requestEntitiesMetricsOptions('name', ['tags.description', 'tags.documentation'], null, null, null, {tags:'*',limit:15})
    change-field = metric
```

Below is content of the dropdown.

![](images/options:fieldPath:array.png)



#### <a name=optionsCallback></a> Callback _(optional, type:function)_

`callback` can be used for manual processing of the descriptors, which are passed as parameters. If `callback` is specified, `valueFieldPath` and `textFieldPath` are ignored. Function should return array of objects, representing options:

```
[
...
{
  value: string,
  text: string
}
...
]
```


[ChartLab Example](https://apps.axibase.com/chartlab/df616dfa/26/)

To fill dropdown with options in which values are names of metrics, collected for the entity, and texts are changed values of the `description` tag we can use th funciton as follows.

```
  [dropdown]
    change-field = metric

    options = javascript: requestEntitiesMetricsOptions(null, null, function(metrics) {
    options =      return metrics.map(function(m) {
    options =        return {
    options =      		value: m.name,
    options =      		text: m.tags.description.replace('Gross Capital Stock', 'GCS')
    options =      	}
    options =      });
    options =    }, null, null, {tags:'*',limit:15})
```

Below is content of the dropdown.

![](images/options_callback.png)



