# tall

[![npm version](https://img.shields.io/npm/v/tall)](https://npm.im/tall)
[![Build Status](https://github.com/lmammino/tall/workflows/main/badge.svg)](https://github.com/lmammino/tall/actions?query=workflow%3Amain)
[![codecov.io](https://codecov.io/gh/lmammino/tall/coverage.svg?branch=master)](https://codecov.io/gh/lmammino/tall)
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)
[![Written in TypeScript](https://badgen.net/badge/-/TypeScript?icon=typescript&label&labelColor=blue&color=555555)](https://www.typescriptlang.org/)

Promise-based, No-dependency URL unshortner (expander) module for Node.js 12+.

**Note**: This library is written in **TypeScript** and type definitions are provided.


## Install

Using npm

```bash
npm install --save tall
```

or with yarn

```bash
yarn add tall
```

## Usage

ES6+ usage:

```javascript
import { tall } from 'tall'

tall('http://www.loige.link/codemotion-rome-2017')
  .then(unshortenedUrl => console.log('Tall url', unshortenedUrl))
  .catch(err => console.error('AAAW 👻', err))
```

With Async await:

```javascript
import { tall } from 'tall';

async function someFunction() {
  try {
    const unshortenedUrl = await tall('http://www.loige.link/codemotion-rome-2017');
    console.log('Tall url', unshortenedUrl);
  } catch (err) {
    console.error('AAAW 👻', err);
  }
}

someFunction();
```

ES5:

```javascript
var { tall } = require('tall')
tall('http://www.loige.link/codemotion-rome-2017')
  .then(function(unshortenedUrl) {
    console.log('Tall url', unshortenedUrl)
  })
  .catch(function(err) {
    console.error('AAAW 👻', err)
  })
```

## Options

It is possible to specify some options as second parameter to the `tall` function.

Available options are the following:

- `method` (default `"GET"`): any available HTTP method
- `maxRedirects` (default `3`): the number of maximum redirects that will be followed in case of multiple redirects.
- `headers` (default `{}`): change request headers - e.g. `{'User-Agent': 'your-custom-user-agent'}`
- `timeout`: (default: `120000`): timeout in milliseconds after which the request will be cancelled

In addition, any other options available on [http.request()](`https://nodejs.org/api/http.html#httprequestoptions-callback`) or `https.request()` are accepted. This for example includes `rejectUnauthorized` to disable certificate checks.

Example:

```javascript
import { tall } from 'tall'

tall('http://www.loige.link/codemotion-rome-2017', {
  method: 'HEAD',
  maxRedirect: 10
})
  .then(unshortenedUrl => console.log('Tall url', unshortenedUrl))
  .catch(err => console.error('AAAW 👻', err))
```

## Contributing

Everyone is very welcome to contribute to this project.
You can contribute just by submitting bugs or suggesting improvements by
[opening an issue on GitHub](https://github.com/lmammino/tall/issues).

## License

Licensed under [MIT License](LICENSE). © Luciano Mammino.
