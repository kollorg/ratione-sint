# @kollorg/ratione-sint <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

Define a data property on an object. Will fall back to assignment in an engine without descriptors.

The three `non*` argument can also be passed `null`, which will use the existing state if available.

The `loose` argument will mean that if you attempt to set a non-normal data property, in an environment without descriptor support, it will fall back to normal assignment.

## Usage

```javascript
var defineDataProperty = require('@kollorg/ratione-sint');
var assert = require('assert');

var obj = {};
defineDataProperty(obj, 'key', 'value');
defineDataProperty(
	obj,
	'key2',
	'value',
	true, // nonEnumerable, optional
	false, // nonWritable, optional
	true, // nonConfigurable, optional
	false // loose, optional
);

assert.deepEqual(
	Object.getOwnPropertyDescriptors(obj),
	{
		key: {
			configurable: true,
			enumerable: true,
			value: 'value',
			writable: true,
		},
		key2: {
			configurable: false,
			enumerable: false,
			value: 'value',
			writable: true,
		},
	}
);
```

[package-url]: https://npmjs.org/package/@kollorg/ratione-sint
[npm-version-svg]: https://versionbadg.es/ljharb/@kollorg/ratione-sint.svg
[deps-svg]: https://david-dm.org/ljharb/@kollorg/ratione-sint.svg
[deps-url]: https://david-dm.org/ljharb/@kollorg/ratione-sint
[dev-deps-svg]: https://david-dm.org/ljharb/@kollorg/ratione-sint/dev-status.svg
[dev-deps-url]: https://david-dm.org/ljharb/@kollorg/ratione-sint#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@kollorg/ratione-sint.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@kollorg/ratione-sint.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@kollorg/ratione-sint.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@kollorg/ratione-sint
[codecov-image]: https://codecov.io/gh/ljharb/@kollorg/ratione-sint/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/ljharb/@kollorg/ratione-sint/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/ljharb/@kollorg/ratione-sint
[actions-url]: https://github.com/kollorg/ratione-sint/actions
