# User Defined Functions

## Overview

This document describes how to define custom time series functions and apply them in chart configurations.

## Window Functions

Use window functions to perform scalar calculations which do not require access to the series object.

Define a custom JavaScript function in the `window` object using the `script` / `endscript` section in the configuration text.

```ls
script
  window.checkRange = function (val) {
     if (val < 0) {
       return 0;
     }
     return false;
  };
endscript
```

Access a custom window function in any field that supports functions by referencing the function by name, for example, the `value` field or the `format` field.

```ls
value = return checkRange(value);
```

## Function Libraries

Load custom JavaScript functions into the configuration with the `import` keyword, followed by package name and the URL of the file containing function definitions.

```ls
import package_name = url
```

Load multiple function files by assigning different package names to each one.

```ls
import package_1 = url_1
import package_2 = url_2
```

When importing multiple files, assign a **unique** package name to each library to avoid collisions.

Load function files from either local or remote server.

### Loading from Remote Server

```ls
# load functions from a remote server
import fred = https://raw.githubusercontent.com/axibase/charts/master/resources/fred.js
```

> Note that configurations loaded over the **HTTP** protocol cannot load function files from **HTTPS** URLs.

* Econometric function [example](https://apps.axibase.com/chartlab/d220468d/19)
* Sun altitude function [example](https://apps.axibase.com/chartlab/8e2917e2/8/)

### Loading from Local Server

If the URL path is relative, the base directory is `/portal/resource/`.

Example:

```ls
import fred = udf_fred.js
```

The above `js` file is loaded from `/portal/resource/udf_fred.js` and must be located at the `/opt/atsd/atsd/conf/portal/udf_fred.js` path in ATSD.

On the ATSD server, the `/opt/atsd/atsd/conf/portal/` directory is mapped to `/portal/resource/` path. The subdirectories are mapped correspondingly, for example:

* `/opt/atsd/atsd/conf/portal/scripts/` -> `/portal/resource/scripts/`.
* `/opt/atsd/atsd/conf/portal/css/` -> `/portal/resource/css/`.

## Usage

Reference the imported function in a `value` expression by specifying the package name, the function name, and the function arguments.

```ls
# Calculate monthly change for series with alias 'raw'
value = fred.MonthlyChange('raw')
```

[ChartLab Example](https://apps.axibase.com/chartlab/d220468d/19)

## Examples

The following sample functions are implemented in the [fred.js](https://apps-chartlab.axibase.com/portal/resource/scripts/fred.js) file.

| **Function Name** | **Arguments** |
|-------------|----------------------|
| [`MonthlyChange`](https://apps.axibase.com/chartlab/d220468d/22/) | alias |
| [`ChangeFromYearAgo`](https://apps.axibase.com/chartlab/d220468d/23/) | alias |
| [`ChangeByOffset`](https://apps.axibase.com/chartlab/d220468d/27/) | alias, [interval](https://axibase.com/products/axibase-time-series-database/visualization/end-time/) |
| [`MonthlyPercentChange`](https://apps.axibase.com/chartlab/d220468d/25/) | alias |
| [`PercentChangeFromYearAgo`](https://apps.axibase.com/chartlab/d220468d/26/) | alias |
| [`PercentChangeByOffset`](https://apps.axibase.com/chartlab/d220468d/28/) | alias, [interval](https://axibase.com/products/axibase-time-series-database/visualization/end-time/) |
| [`CompoundedAnnualRateOfChange`](https://apps.axibase.com/chartlab/d220468d/29/) | alias |
| [`ContinuouslyCompoundedRateOfChange`](https://apps.axibase.com/chartlab/d220468d/30/) | alias |
| [`NaturalLog`](https://apps.axibase.com/chartlab/d220468d/31/) |  alias |
| [`IndexMax`](https://apps.axibase.com/chartlab/d220468d/32/) | alias |
| [`Index`](https://apps.axibase.com/chartlab/d220468d/33/) | alias, [time](https://axibase.com/products/axibase-time-series-database/visualization/end-time/) |

[Summary Example](https://apps.axibase.com/chartlab/d220468d/34)

## Deploying Function Files

On the ATSD server, function files are stored in the following directory:

```txt
/opt/atsd/atsd/conf/portal/scripts
```

The JavaScript files placed into this directory are accessible by file name:

```ls
import fred = fred_v1.js
```

Server restart is **not** required to access new or updated function files.

## Writing Functions

The function declaration must start with `exports.` followed by a valid function name. Function names are case-sensitive.

The function can have any number of arguments however the first argument must be the alias of the series to which the function applies.

The current value can be accessed with `value(alias)` method.

```javascript
exports.NaturalLog = function (alias) {
    var currentValue = value(alias);
    return Math.log(currentValue);
};
```

The function definition must start with the `exports.` qualifier and implemented as a JavaScript [function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions).

The function must return a numeric value or `null` if the result cannot be computed.

```javascript
exports.devideBy = function (alias, num) {
  if (num == 0) {
    //if num is zero, return null
    return null;
  }
  var result = value(alias) / num;
  return result;
};
```

The function body can reference any JavaScript function such as [`Math`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math), [built-in functions, supported in the value setting](value_functions.md), [utility functions](#utility-functions) listed below.

```javascript
exports.getValueRange = function (alias, period) {
  // get the maximum value within the current period
  var maxAtPeriod = max(alias, period);
  // get the minimum value within the current period
  var minAtPeriod = min(alias, period);
  // calculate the difference between maximum and minumum values
  var result = maxAtPeriod - minAtPeriod;
  // return the result to the calling function
  return result;
};
```

See additional function examples in [`examples.js`](../resources/examples.js).

**ChartLab** examples:

* [`getValueRange`](https://apps.axibase.com/chartlab/2595a144/1/)
* [`getDifferenceFromAverage`](https://apps.axibase.com/chartlab/2595a144/2/)
* [`getWeight`](https://apps.axibase.com/chartlab/2595a144/3/)

## Example

This example illustrates how to develop and deploy a basic user-defined function. For the purpose of this exercise, create a function that multiplies original values by a specified constant value.

### Step 1. Create JavaScript File

Name the new function `multiplyBy`. The function accepts series alias as the first argument and a numeric constant as the second argument.

Create a file `my_math.js` and store the below function definition in the file.

```javascript
/*
 This function multiples all values in the original series, identified with the alias parameter, by a constant numeric value.
*/
exports.multiplyBy = function (alias, num) {
  // multiply current value from the referenced series by number 'num'
  var result = value(alias) * num;
  // return the product to the calling function
  return result;
};
```

### Step 2. Copy JavaScript File into ATSD

Copy the `my_math.js` file to the `/opt/atsd/atsd/conf/portal/scripts` directory in the ATSD server.

Verify that the file is accessible at the following URL: `http://atsd_hostname:8443/portal/resource/scripts/my_math.js`.

### Step 3. Import Functions

Open the **Portals > Configure** page in the top menu and create a new portal.

Enter the following configuration text. Replace `cpu_busy` and `nurswgvml007` with a metric and an entity present in your ATSD instance.

```ls
[configuration]
  height-units = 2
  width-units = 2
  import mm = my_math.js

[group]
  [widget]
    type = chart
    timespan = 1 hour
    [series]
      metric = cpu_busy
      entity = nurswgvml007
      alias = s1
    [series]
      value = mm.multiplyBy('s1', 2)
```

Save the portal. View the portal to check results.

[ChartLab Example](https://apps.axibase.com/chartlab/bc36b341)

## Utility Functions

### `getValueWithOffset()`

Get the value of the series, identified by `alias`, for the `timestamp`, which is calculated as `current_time - offset`, where  `current_time` is the time of currently processed sample. If there is no sample with such `timestamp`, the value is linearly interpolated from neighboring samples.

[ChartLab Example](https://apps.axibase.com/chartlab/2595a144/4/)

* Syntax

```javascript
getValueWithOffset(alias, offset)
```

| **Argument** | **Required** | **Type** | **Description** |
|------|-----------|------|-------------|
| alias | yes | string | Alias of the series, from which the value is retrieved. |
| offset | yes | string | Offset, with which the previous value is retrieved, specified as interval, for example '1 day'. |

### `getValueForDate()`

Get the value of the series, identified by `alias`, for the specified `datetime`.
If there is no sample recorded for the specified `datetime`, the value is linearly interpolated from the neighboring samples.

[ChartLab Example](https://apps.axibase.com/chartlab/2595a144/5/)

* Syntax

```javascript
getValueForDate(alias, datetime)
```

| **Argument** | **Required** | **Type** | **Description** |
|------|-----------|------|-------------|
| alias | yes | string | Alias of the series, from which the value is retrieved. |
| datetime | yes | string | Time, for which value is retrieved. Can be specified as local time, ISO time, or using an [`end_time`](https://axibase.com/products/axibase-time-series-database/visualization/end-time/) expression. |

### `getMaximumValue()`

Get the maximum value of the series, identified by `alias`, for the loaded timespan.

[![](./images/button.png)](https://apps.axibase.com/chartlab/2595a144/6/)

* Syntax

```javascript
getMaximumValue(alias)
```

| **Argument** | **Required** | **Type** | **Description** |
|------|-----------|------|-------------|
| alias | yes | string | Alias of the series, from which the value is retrieved. |
