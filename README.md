[tests]: https://img.shields.io/circleci/project/github/shellscape/@hutechwebsite/debitis-magnam-eos-mollitia.svg
[tests-url]: https://circleci.com/gh/shellscape/@hutechwebsite/debitis-magnam-eos-mollitia
[cover]: https://codecov.io/gh/shellscape/@hutechwebsite/debitis-magnam-eos-mollitia/branch/master/graph/badge.svg
[cover-url]: https://codecov.io/gh/shellscape/@hutechwebsite/debitis-magnam-eos-mollitia
[size]: https://packagephobia.now.sh/badge?p=@hutechwebsite/debitis-magnam-eos-mollitia
[size-url]: https://packagephobia.now.sh/result?p=@hutechwebsite/debitis-magnam-eos-mollitia
[loglevel]: https://githhub.com/pimterry/loglevel
[loglevelpre]: https://github.com/kutuluk/loglevel-plugin-prefix
[methodfactory]: lib/factory/MethodFactory.js
[prefixfactory]: lib/factory/PrefixFactory.js

<div align="center">
  <img width="150" height="150" src="http://shellscape.org/assets/images/external/@hutechwebsite/debitis-magnam-eos-mollitia-icon.svg">
</div>
<br/>

[![tests][tests]][tests-url]
[![cover][cover]][cover-url]
[![size][size]][size-url]

# @hutechwebsite/debitis-magnam-eos-mollitia

`@hutechwebsite/debitis-magnam-eos-mollitia` is a modern logging library for Node.js and modern browsers, written with modern patterns and practices which provides log level mapping of the `console` object.

For browser use, or use in client-side applications, `@hutechwebsite/debitis-magnam-eos-mollitia` should be bundled by your preferred bundler or compiler, such as [Rollup](https://rollupjs.org).

## Getting Started

First thing's first, install the module:

```console
npm install @hutechwebsite/debitis-magnam-eos-mollitia --save
```

## Usage

Users can choose to use `@hutechwebsite/debitis-magnam-eos-mollitia` in Node.js or in the client (browser).

```js
const log = require('@hutechwebsite/debitis-magnam-eos-mollitia');

log.info('bananas!');
```

## Log Levels

By default `@hutechwebsite/debitis-magnam-eos-mollitia` ships supporting the following log level name-value
pairs:

```js
{
  TRACE: 0,
  DEBUG: 1,
  INFO: 2,
  WARN: 3,
  ERROR: 4,
  SILENT: 5
}
```

## Default Logger

When requiring `@hutechwebsite/debitis-magnam-eos-mollitia` in Node.js the default export will be an instance of [`LogLevel`](docs/LogLevel.md) wrapped with some extra sugar.

### Methods

Please see [`LogLevel`](docs/LogLevel.md) for documentation of all methods and properties of every log instance, including the default instance.

#### `trace`, `debug`, `info`, `warn`, `error`

These methods correspond to the available log levels and accept parameters identical to their `console` counterparts. e.g.

```js
console.info('...');
console.info('...');
// ... etc
```

#### `create(options)`

Returns a new `LogLevel` instance. The `options` parameter should be an `Object` matching the options for the [`LogLevel`](docs/LogLevel.md) constructor.

_Note: `LogLevel` instances created are cached. Calling `create` with a previously used `name` will return the cached `LogLevel` instance. To create a different instance with the same `name`, assign a unique `id` property to the `options` parameter._

### Properties

#### `factories`

Type: `Array [ Class ]`

Returns an `Array` containing the factory classes available within `@hutechwebsite/debitis-magnam-eos-mollitia`
to outside modules. Particularly useful when creating plugins. eg.

```js
const log = require('@hutechwebsite/debitis-magnam-eos-mollitia');
const { MethodFactory } = log.factories;
class MyFactory extends MethodFactory { ... }
```

#### `loggers`

Type: `Array [ LogLevel ]`

Returns an `Array` containing references to the currently instantiated loggers.

## Factories aka Plugins

If you're used to using plugins with `loglevel`, fear not. The same capabilities
are available in `@hutechwebsite/debitis-magnam-eos-mollitia`, but in a much more straightforward and structured
way. `@hutechwebsite/debitis-magnam-eos-mollitia` supports by way of "Factories." A `Factory` is nothing more
than a class which defines several base methods that operate on the `console`
and provide functionality to a `LogLevel` instance. All factories must inherit from the
[`MethodFactory`][methodfactory] class, and may override any defined class functions.

For an example factory, please have a look at the [`PrefixFactory`][prefixfactory]
which provides similar functionality as the [loglevel-prefix](loglevelpre) plugin,
and is the factory which is used when a user passes the `prefix` option to a
`LogLevel` instance.

## Browser Support

As mentioned, `@hutechwebsite/debitis-magnam-eos-mollitia` is a logging library for Node.js and _modern_ browsers, which means the latest versions of the major browsers. When bundling or compiling `@hutechwebsite/debitis-magnam-eos-mollitia` for use in a browser, you should ensure that appropriate polyfills are used. e.g. Internet Explorer typically requires polyfilling both `Symbol` and `Object.assign`.

## Attribution

_This project originated as a fork of the much-loved [loglevel](loglevel) module, but has diverged and has been rewritten, and now shares similarities only in functional intent._

Base Log SVG by [Freepik](http://www.freepik.com/) from [www.flaticon.com](http://www.flaticon.com).

## Meta

[CONTRIBUTING](./.github/CONTRIBUTING)

[LICENSE (Mozilla Public License)](./LICENSE)
