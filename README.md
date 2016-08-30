# [React] Server render

[![Build Status](https://travis-ci.org/alt-j/react-server.svg?branch=master)](https://travis-ci.org/alt-j/react-server)
[![dependencies Status](https://david-dm.org/alt-j/react-server/status.svg)](https://david-dm.org/alt-j/react-server)
[![devDependencies Status](https://david-dm.org/alt-j/react-server/dev-status.svg)](https://david-dm.org/alt-j/react-server?type=dev)
[![Coverage Status](https://coveralls.io/repos/github/alt-j/react-server/badge.svg?branch=master)](https://coveralls.io/github/alt-j/react-server?branch=master)

The module for rendering react-element in the server **12 times as fast** (see [benchmarks](https://github.com/alt-j/react-server-benchmark)) as [traditional react rendering](https://facebook.github.io/react/docs/environments.html) (in production mode).

## Quick start
```sh
npm install react-server-rendering
```

```js
var react = require('react-server-rendering');

// All declarations must be transformed from jsx to js.
// Also you must remove all propTypes (in case of babel, you can use transform-react-remove-prop-types).
var component = react.createClass({
    getDefaultProps: function () {
        return {
            content: 'Some <b>bold</b> text'
        };
    },

    render: function () {
        return React.createElement('div', {
            className: 'text',
            dangerouslySetInnerHTML: { __html: this.props.content }
        });
    }
})

// After that all declarations transformed to the functions,
// which receive props and returns string.
console.log(react.createElement(component));
```


## What's inside?
High speed mock for react, which doesn't use any abstraction and transform all of your declarations to html (string) generators.

For the sake of speed, wasn't implemented some features:
- Context.
