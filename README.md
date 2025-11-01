# @louwers/bws.js

FreeBSD builds of [uWebSockets.js](https://github.com/uNetworking/uWebSockets.js) - a highly scalable WebSocket & HTTP server for Node.js.

> [!IMPORTANT]  
> This project is not affiliated with [uWebSockets.js](https://github.com/uNetworking/uWebSockets.js). FreeBSD is not an officially supported platform.

## About

This repository exists to build FreeBSD binaries for uWebSockets.js, which are distributed as `@louwers/bws.js` in the GitHub npm registry. Upstream builds for Linux, macOS, and Windows are also included in the package.

## Installation

```bash
npm install @louwers/bws.js
```

The package is hosted in the GitHub npm registry. For instructions on authenticating with the GitHub npm registry, see the [GitHub documentation](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-npm-registry#authenticating-with-a-personal-access-token).

## Usage

```javascript
const uWS = require('@louwers/bws.js');

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

## License

Apache-2.0 (same as uWebSockets.js)
