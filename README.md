# React Chartkick

Create beautiful JavaScript charts with one line of React

[See it in action](https://www.chartkick.com/react)

Supports [Chart.js](https://www.chartjs.org/), [Google Charts](https://developers.google.com/chart/), and [Highcharts](https://www.highcharts.com/)

## Quick Start

Run

```sh
npm install react-chartkick chart.js
```

And add

```javascript
import { LineChart, PieChart } from 'react-chartkick'
import 'chartkick/chart.js'
```

This sets up Chartkick with Chart.js. For other charting libraries, see [detailed instructions](#installation).

## Charts

Line chart

```jsx
<LineChart data={{"2021-01-01": 11, "2021-01-02": 6}} />
```

Pie chart

```jsx
<PieChart data={[["Blueberry", 44], ["Strawberry", 23]]} />
```

Column chart

```jsx
<ColumnChart data={[["Sun", 32], ["Mon", 46], ["Tue", 28]]} />
```

Bar chart

```jsx
<BarChart data={[["Work", 32], ["Play", 1492]]} />
```

Area chart

```jsx
<AreaChart data={{"2021-01-01": 11, "2021-01-02": 6}} />
```

Scatter chart

```jsx
<ScatterChart data={[[174.0, 80.0], [176.5, 82.3]]} xtitle="Size" ytitle="Population" />
```

Geo chart - *Google Charts*

```jsx
<GeoChart data={[["United States", 44], ["Germany", 23], ["Brazil", 22]]} />
```

Timeline - *Google Charts*

```jsx
<Timeline data={[["Washington", "1789-04-29", "1797-03-03"], ["Adams", "1797-03-03", "1801-03-03"]]} />
```

Multiple series

```javascript
data = [
  {name: "Workout", data: {"2021-01-01": 3, "2021-01-02": 4}},
  {name: "Call parents", data: {"2021-01-01": 5, "2021-01-02": 3}}
];
```

and

```jsx
<LineChart data={data} />
```

## Data

Data can be an array, object, callback, or URL.

#### Array

```jsx
<LineChart data={[["2021-01-01", 2], ["2021-01-02", 3]]} />
```

#### Object

```jsx
<LineChart data={{"2021-01-01": 2, "2021-01-02": 3}} />
```

#### Callback

```javascript
function fetchData(success, fail) {
  success({"2021-01-01": 2, "2021-01-02": 3})
  // or fail("Data not available")
}
```

and

```jsx
<LineChart data={fetchData} />
```

#### URL

Make your pages load super fast and stop worrying about timeouts. Give each chart its own endpoint.

```jsx
<LineChart data="/stocks" />
```

## Options

Id, width, and height

```jsx
<LineChart id="users-chart" width="800px" height="500px" />
```

Min and max values

```jsx
<LineChart min={1000} max={5000} />
```

`min` defaults to 0 for charts with non-negative values. Use `null` to let the charting library decide.

Min and max for x-axis - *Chart.js*

```jsx
<LineChart xmin="2021-01-01" xmax="2022-01-01" />
```

Colors

```jsx
<LineChart colors={["#b00", "#666"]} />
```

Stacked columns or bars

```jsx
<ColumnChart stacked={true} />
```

Discrete axis

```jsx
<LineChart discrete={true} />
```

Label (for single series)

```jsx
<LineChart label="Value" />
```

Axis titles

```jsx
<LineChart xtitle="Time" ytitle="Population" />
```

Straight lines between points instead of a curve

```jsx
<LineChart curve={false} />
```

Show or hide legend

```jsx
<LineChart legend={true} />
```

Specify legend position

```jsx
<LineChart legend="bottom" />
```

Donut chart

```jsx
<PieChart donut={true} />
```

Prefix, useful for currency - *Chart.js, Highcharts*

```jsx
<LineChart prefix="$" />
```

Suffix, useful for percentages - *Chart.js, Highcharts*

```jsx
<LineChart suffix="%" />
```

Set a thousands separator - *Chart.js, Highcharts*

```jsx
<LineChart thousands="," />
```

Set a decimal separator - *Chart.js, Highcharts*

```jsx
<LineChart decimal="," />
```

Set significant digits - *Chart.js, Highcharts*

```jsx
<LineChart precision={3} />
```

Set rounding - *Chart.js, Highcharts*

```jsx
<LineChart round={2} />
```

Show insignificant zeros, useful for currency - *Chart.js, Highcharts*

```jsx
<LineChart round={2} zeros={true} />
```

Friendly byte sizes - *Chart.js*

```jsx
<LineChart bytes={true} />
```

Specify the message when the chart is loading

```jsx
<LineChart loading="Loading..." />
```

Specify the message when data is empty

```jsx
<LineChart empty="No data" />
```

Refresh data from a remote source every `n` seconds

```jsx
<LineChart refresh={60} />
```

You can pass options directly to the charting library with:

```jsx
<LineChart library={{backgroundColor: "#eee"}} />
```

See the documentation for [Google Charts](https://developers.google.com/chart/interactive/docs/gallery), [Highcharts](https://api.highcharts.com/highcharts), and [Chart.js](https://www.chartjs.org/docs/) for more info.

To customize datasets in Chart.js, use:

```jsx
<LineChart dataset={{borderWidth: 10}} />
```

You can pass this option to individual series as well.

### Global Options

To set options for all of your charts, use:

```javascript
Chartkick.options = {
  colors: ["#b00", "#666"]
}
```

### Multiple Series

You can pass a few options with a series:

- `name`
- `data`
- `color`
- `dataset` - *Chart.js only*
- `points` - *Chart.js only*
- `curve` - *Chart.js only*

### Download Charts

*Chart.js only*

Give users the ability to download charts. It all happens in the browser - no server-side code needed.

```jsx
<LineChart download={true} />
```

Set the filename

```jsx
<LineChart download="boom" />
```

**Note:** Safari will open the image in a new window instead of downloading.

Set the background color

```jsx
<LineChart download={{background: "#fff"}} />
```

## Installation

### Chart.js

Run

```sh
npm install react-chartkick chart.js
```

And add

```javascript
import { LineChart, PieChart } from 'react-chartkick'
import 'chartkick/chart.js'
```

### Google Charts

Run

```sh
npm install react-chartkick
```

And add

```javascript
import Chartkick, { LineChart, PieChart } from 'react-chartkick'
```

And include on the page

```html
<script src="https://www.gstatic.com/charts/loader.js"></script>
```

To specify a language or Google Maps API key, use:

```js
Chartkick.configure({language: "de", mapsApiKey: "..."})
```

### Highcharts

Run

```sh
npm install react-chartkick highcharts
```

And add

```javascript
import { LineChart, PieChart } from 'react-chartkick'
import 'chartkick/highcharts'
```

### No Package Manager

Include the charting library and the Chartkick library

```html
<script src="https://unpkg.com/chart.js@3.4.1"></script>
<script src="https://unpkg.com/chartjs-adapter-date-fns@2.0.0/dist/chartjs-adapter-date-fns.bundle.js"></script>
<script src="https://unpkg.com/chartkick@4.0.5"></script>
<script src="https://unpkg.com/react-chartkick@0.5.2"></script>
```

Charts are prefixed with `ReactChartkick`, like `ReactChartkick.LineChart`.

### Multiple Libraries

If more than one charting library is loaded, choose between them with:

```jsx
<LineChart adapter="google" />
```

Options are `google`, `highcharts`, and `chartjs`

## Upgrading

### 0.5.0

For the no package manager install, Chartkick.js is no longer bundled, allowing you to update them independently. Include it manually before React Chartkick.

```html
<script src="https://unpkg.com/chartkick@4.0.2"></script>
````

## History

View the [changelog](https://github.com/ankane/react-chartkick/blob/master/CHANGELOG.md)

## Contributing

Everyone is encouraged to help improve this project. Here are a few ways you can help:

- [Report bugs](https://github.com/ankane/react-chartkick/issues)
- Fix bugs and [submit pull requests](https://github.com/ankane/react-chartkick/pulls)
- Write, clarify, or fix documentation
- Suggest or add new features

To get started with development, run:

```sh
git clone https://github.com/ankane/react-chartkick.git
cd react-chartkick
npm install
npm run build
```
