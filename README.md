# carma-tap-webpack

> add [Karma][karma], [TAP][tap] and [webpack][webpack] boilerplate test settings to projects

[karma]: http://karma-runner.github.io/1.0/index.html
[tap]: https://testanything.org/
[webpack]: https://webpack.github.io/

Setting `Karma` with many plugins it is a time consuming process, many hours of trial and error.

## What's include ?
* [karma-tap](https://github.com/tmcw-up-for-adoption/karma-tap), karma TAP adapter.
* [karma-tap-pretty-reporter](https://github.com/bySabi/karma-tap-pretty-reporter) cause everyone need a nice output. See supported [prettifiers](https://github.com/bySabi/karma-tap-pretty-reporter#supported-prettifiers)
* [tape](https://github.com/substack/tape) for test harness on node and browsers.
* [tap-lochness](https://github.com/bySabi/tap-lochnest) for nested TAP test.
* karma browser launchers `karma-chrome-launcher`, `karma-jsdom-launcher`, ...
* [webpack](https://webpack.github.io/) and [karma-webpack](https://github.com/webpack/karma-webpack)

## Why `webpack` is needed for test?
* When we test code on browsers at the end we will need bundle sources, test files and assets. Other solutions can be use like `browserify`. We opinionated on `webpack`
* When Hot Module Replacement (HMR) is needed, webpack is the way to go.
* On Karma `autowatch` mode, for a good performance, a robust cache and rebuild solution is needed, `webpack` is best on this apart.

## Why all `karma` complex setup, why not just use the very simple [tape](https://github.com/substack/tape)?
If your project tests need
* browsers launch/switch/management
* file bundle
* file watch mode

Karma will provide it!

## Install

### npm

```bash
npm install karma bySabi/carma-tap-webpack --save-dev
```

### add `karma.conf.js` to project folder
```js
var carma = require('carma-tap-webpack');

module.exports = function(config) {
  carma(config);
  config.set({
    // override settings
  });
}
```

Custom karma settings can be add or defaults can be override. Default `carma-tap-webpack` [karma.conf.js][karmaconfjs]

[karmaconfjs]: ./karma.conf.js

### add karma and test scripts to `package.json`
```json
  "scripts": {
    "karma": "karma start",
    "testonly:jsdom": "cross-env JSDOM=true npm run karma",
    "testonly:chrome": "npm run karma",
    "testonly": "npm run testonly:chrome",
    "test": "npm run testonly"
  },
```

## Contributing

* Documentation improvement
* Feel free to send any PR

## License

[ISC][isc-license]

[isc-license]:./LICENSE
