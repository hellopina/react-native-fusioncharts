#### [Demos and Documentation](https://fusioncharts.github.io/react-native-fusioncharts/)

# react-native-fusioncharts

A `React Native` component which provides bindings for `FusionCharts` JavaScript Charting Library. It easily adds rich and interactive charts to any `React Native` Projects.

## Installation

To install `react-native-fusioncharts`, run:

```bash
$ npm install --save react-native-fusioncharts
```

After installing `react-native-fusioncharts`, follow the steps below:

### For Android

* create `assets` folder in `android/app/src/main` directory if it doesn't exist,
* copy `fusioncharts` library into `assets` folder (in most cases copy `node_modules/fusioncharts` folder),
* create a file named `fuioncharts.html` in this `assets` folder with following content:

The `android/app/src/main/assets/fuioncharts.html` file:

```html
<!DOCTYPE html>
<html>

<head>
  <title>FusionCharts</title>
  <meta http-equiv="content-type" content="text/html; charset=utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />

  <style type="text/css">
    body,
    html {
      margin: 0;
      padding: 0;
      overflow: hidden;
      font-size: 13px;
    }

    #chart-container {
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      position: absolute;
      user-select: none;
      -webkit-user-select: none;
      overflow: hidden;
    }

    #loading-text {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      -webkit-transform: translate(-50%, -50%);
      user-select: none;
      -webkit-user-select: none;
    }
  </style>
</head>

<body>
  <div id="chart-container">
    <div id="loading-text">
      Chart is loading...
    </div>
  </div>

  <script type='text/javascript'>
    "use strict"; (function () { var a = Promise.resolve(), b = {}, c = {}; (function d() { var f = function () { function g() { return Math.floor(65536 * (1 + Math.random())).toString(16).substring(1) } return g() + g() + "-" + g() + "-" + g() + "-" + g() + "-" + g() + g() + g() }; window.webViewBridge = { send: function send(g, h, i, j) { i = i || function () { }, j = j || function () { }; var k = { targetFunc: g, data: h || {}, msgId: f() }, l = JSON.stringify(k); a = a.then(function () { return new Promise(function (m, n) { b[k.msgId] = { resolve: m, reject: n }, c[k.msgId] = { onsuccess: i, onerror: j }, window.postMessage(l) }) }).catch(function () { }) } }, window.document.addEventListener("message", function (g) { var h; try { h = JSON.parse(g.data) } catch (i) { return } b[h.msgId] && (b[h.msgId].resolve(), delete b[h.msgId]), h.args && c[h.msgId] && (h.isSuccessfull ? c[h.msgId].onsuccess.apply(null, h.args) : c[h.msgId].onerror.apply(null, h.args), delete c[h.msgId]) }) })() })();
  </script>

  <!-- Here include the required fusioncharts modules -->
  <script type='text/javascript' src="fusioncharts/fusioncharts.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.charts.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.gantt.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.powercharts.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.ssgrid.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.treemap.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.widgets.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.zoomscatter.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.maps.js"></script>
  <script type='text/javascript' src="fusioncharts/maps/fusioncharts.usa.js"></script>
  <script type='text/javascript' src="fusioncharts/maps/fusioncharts.world.js"></script>
  <script type='text/javascript' src="fusioncharts/themes/fusioncharts.theme.fint.js"></script>
  <script type='text/javascript' src="fusioncharts/themes/fusioncharts.theme.ocean.js"></script>
  <script type='text/javascript' src="fusioncharts/themes/fusioncharts.theme.zune.js"></script>
  <script type='text/javascript' src="usioncharts/themes/fusioncharts.theme.carbon.js"></script>
</body>

</html>
```

* set `libraryPath` property to the `FusionCharts` component as follows:

```html
<FusionCharts
  ......

  libraryPath={{ uri: 'file:///android_asset/fusioncharts.html' }}
 />
```

### For iOS

* create `assets` folder in your project root if it doesn't exist,
* copy `fusioncharts` library into this `assets` folder (requires only when the licensed version of fusioncharts is used),
* create a file named `fuioncharts-tpl.html` in this `assets` folder with following content:

The `./assets/fuioncharts-tpl.html` file:

```html
<!DOCTYPE html>
<html>

<head>
  <!-- Here include the required fusioncharts modules -->
  <script type='text/javascript' src="fusioncharts/fusioncharts.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.charts.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.gantt.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.powercharts.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.ssgrid.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.treemap.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.widgets.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.zoomscatter.js"></script>
  <script type='text/javascript' src="fusioncharts/fusioncharts.maps.js"></script>
  <script type='text/javascript' src="fusioncharts/maps/fusioncharts.usa.js"></script>
  <script type='text/javascript' src="fusioncharts/maps/fusioncharts.world.js"></script>
  <script type='text/javascript' src="fusioncharts/themes/fusioncharts.theme.fint.js"></script>
  <script type='text/javascript' src="fusioncharts/themes/fusioncharts.theme.ocean.js"></script>
  <script type='text/javascript' src="fusioncharts/themes/fusioncharts.theme.zune.js"></script>
  <script type='text/javascript' src="fusioncharts/themes/fusioncharts.theme.carbon.js"></script>
</head>

<body></body>

</html>
```

* add a `build:assets` script in your `package.json` file as follows:

In your `package.json` file:

```javascript
  ......

  "scripts": {
    ......

    "build:assets": "fc-build-assets -t ./assets/fusioncharts-tpl.html -l ./assets/fusioncharts"
  },

  ......
```

The `-l ./assets/fusioncharts` option is only required when you copied `fusioncharts` libarary in your `assets` folder.

* set `libraryPath` property to the `FusionCharts` component as follows:

```html
<FusionCharts
  ......

  libraryPath={require('./assets/fusioncharts.html')}
 />
```

* run the following command before running the app:

```bash
$ npm run build:assets
```

## Getting Started

Include the `react-native-fusioncharts` library as follows:

The `App.js` file:

```javascript
import React, { Component } from 'react';
import { AppRegistry, StyleSheet, Text, View, Platform } from 'react-native';
import FusionCharts from 'react-native-fusioncharts';

export default class App extends Component {
  constructor(props) {
    super(props);

    this.state = {
      type: 'column2d',
      width: '100%',
      height: '100%',
      dataFormat: 'json',
      dataSource: {
            "chart": {
                "caption": "Harry's SuperMart",
                "subCaption": "Top 5 stores in last month by revenue",
                "numberprefix": "$",
                "theme": "fint"
            },
            "data": [
                {
                    "label": "Bakersfield Central",
                    "value": "880000"
                },
                {
                    "label": "Garden Groove harbour",
                    "value": "730000"
                },
                {
                    "label": "Los Angeles Topanga",
                    "value": "590000"
                },
                {
                    "label": "Compton-Rancho Dom",
                    "value": "520000"
                },
                {
                    "label": "Daly City Serramonte",
                    "value": "330000"
                }
            ]
        }
    };

    this.libraryPath = Platform.select({
      // Specify fusioncharts.html file location
      ios: require('./assets/fusioncharts.html'),
      android: { uri: 'file:///android_asset/fusioncharts.html' },
    });
  }

  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.heading}>
          FusionCharts Integration with React Native
        </Text>
        <View style={styles.chartContainer}>
          <FusionCharts
            type={this.state.type}
            width={this.state.width}
            height={this.state.height}
            dataFormat={this.state.dataFormat}
            dataSource={this.state.dataSource}
            libraryPath={this.libraryPath} // set the libraryPath property
          />
        </View>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 10
  },
  heading: {
    fontSize: 20,
    textAlign: 'center',
    marginBottom: 10
  },
  chartContainer: {
    height: 200
  }
});

// skip this line if using Create React Native App
AppRegistry.registerComponent('ReactNativeFusionCharts', () => App);
```

## Unit Test

```sh
$ npm test
```

## Contributing

* Clone the repository.
* Install dependencies
* Run `npm start` to start React Native Packager server.
* Run on Android or iOS emulator.

```sh
$ git clone https://github.com/fusioncharts/react-native-fusioncharts.git
$ cd react-native-fusioncharts
$ npm i
$ npm start
$ emulator @<name_of_android_emulator>
$ npm run android [to run on Android platform]
$ npm run ios [to run on iOS platform]
```

To run release version of Android app, run:
```sh
$ npm run android:release
```

To run release version of iOS app, run:
```sh
$ npm run ios:release
```

To generate a signed release Android APK, run:
```sh
$ npm run build:android
```

To generate release iOS app, run:
```sh
$ npm run build:ios
```

### [Demos and Documentation](https://fusioncharts.github.io/react-native-fusioncharts/)