# @louwers/bWebSockets.js

FreeBSD build of [uWebSockets.js](https://github.com/uNetworking/uWebSockets.js) - a highly scalable WebSocket & HTTP server for Node.js.

## Installation

```bash
npm install @louwers/bWebSockets.js
```

## About

This package provides FreeBSD-compatible binary builds of uWebSockets.js. The native `.node` binaries are built specifically for FreeBSD and support multiple Node.js versions.

uWebSockets.js is one of the most performant WebSocket and HTTP server implementations available for Node.js, built on top of the C++ library µWebSockets.

## Usage

```javascript
const uWS = require('@louwers/bWebSockets.js');

const app = uWS.App().get('/*', (res, req) => {
  res.end('Hello World!');
}).listen(9001, (token) => {
  if (token) {
    console.log('Listening to port 9001');
  } else {
    console.log('Failed to listen to port 9001');
  }
});
```

For more examples and documentation, see the [uWebSockets.js repository](https://github.com/uNetworking/uWebSockets.js).

## FreeBSD Support

This package is specifically built for FreeBSD systems. The binaries are compiled using the FreeBSD build workflow maintained at [louwers/uws-freebsd](https://github.com/louwers/uws-freebsd).

## Building

If you need to build the binaries yourself or want to learn more about the build process, visit the [uws-freebsd repository](https://github.com/louwers/uws-freebsd).

## License

Apache-2.0 (same as uWebSockets.js)
