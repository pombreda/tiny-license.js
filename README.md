# tiny-license.js

[![Build Status](https://img.shields.io/travis/shinnn/tiny-license.js.svg?style=flat)](https://travis-ci.org/shinnn/tiny-license.js)
[![Build status](https://ci.appveyor.com/api/projects/status/e0n5bwe7cw089dp2?svg=true)](https://ci.appveyor.com/project/ShinnosukeWatanabe/tiny-license-js)
[![Coverage Status](https://img.shields.io/coveralls/shinnn/tiny-license.js.svg?style=flat)](https://coveralls.io/r/shinnn/tiny-license.js)
[![Dependency Status](https://david-dm.org/shinnn/tiny-license.js.svg?style=flat)](https://david-dm.org/shinnn/tiny-license.js)
[![devDependency Status](https://david-dm.org/shinnn/tiny-license.js/dev-status.svg?style=flat)](https://david-dm.org/shinnn/tiny-license.js#info=devDependencies)

Create a tiny JavaScript license comment from package data

```javascript
var json = {
  name: 'isogram',
  author: 'Shinnosuke Watanabe',
  homepage: 'https://github.com/shinnn/isogram'
};

tinyLicense(json);
//=>
/*!
 * isogram | (c) Shinnosuke Watanabe
 * https://github.com/shinnn/isogram
*/
```

## Installation

[![NPM version](https://img.shields.io/npm/v/tiny-license.svg?style=flat)](https://www.npmjs.com/package/tiny-license)
[![Bower version](https://img.shields.io/bower/v/tiny-license.svg?style=flat)](https://github.com/shinnn/tiny-license.js/releases)

#### [npm](https://www.npmjs.com/)

```sh
npm install tiny-license
```

#### [Bower](http://bower.io/)

```sh
bower install tiny-license
```

#### [Duo](http://duojs.org/)

```javascript
var tinyLicense = require('shinnn/tiny-license.js');
```

## API

### tinyLicense(*packageData* [, *option*])

*packageData*: `Object`  
*option*: `Object`  
Return: `String`

It takes data of a package definition file, like [package.json](https://www.npmjs.org/doc/files/package.json.html) and [bower.json](https://github.com/bower/bower.json-spec), and returns a string of JavaScript block comment which represents the license of the package.

It uses the follwing properties of data:

* `name`
* `author` or `authors`
* `license` or `licenses`
* `homepage`

All of them are optional.

```javascript
var json = {
  name: 'foo',
  authors: [
    'John Smith <bar@email> (baz.com)',
    {
      name: 'Mary Sue',
      email: 'qux@email'
    }
  ],
  license: 'CC0-1.0',
  homepage: 'http://nodejs.org/'
};

tinyLicense(json);
//=>
/*!
 * foo | CC0-1.0 (c) John Smith, Mary Sue
 * http://nodejs.org/
*/

```

#### option.lastNewline

Type: `Boolean`  
Default: `true`

Setting this option `false` removes the last newline from the result.

```javascript
var json = {name: 'foo'};

tinyLicense(json);                       //=> '/*!\n * foo\n*/\n'
tinyLicense(json, {lastNewline: false}); //=> '/*!\n * foo\n*/'
```

## License

Copyright (c) 2014 [Shinnosuke Watanabe](https://github.com/shinnn)

Licensed under [the MIT License](./LICENSE).
