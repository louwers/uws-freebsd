# uws-freebsd

Multi-platform builds of [uWebSockets.js](https://github.com/uNetworking/uWebSockets.js) - a highly scalable WebSocket & HTTP server for Node.js.

## Installation

```bash
npm install @louwers/bws.js
```

## About

This repository provides automated builds of uWebSockets.js for multiple platforms including FreeBSD and Linux. The native `.node` binaries support multiple Node.js versions.

uWebSockets.js is one of the most performant WebSocket and HTTP server implementations available for Node.js, built on top of the C++ library µWebSockets.

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

## Platform Support

This repository builds binaries for:
- **FreeBSD x64** - Built in a FreeBSD VM using Clang 18
- **Linux x64** - Built natively on Ubuntu using Clang

All platforms support multiple Node.js versions (v20, v22, v24, v25).

## Building

### Automated Builds

The workflow can be triggered in two ways:

1. **Manual Dispatch**: Go to the Actions tab and run the "Build and Release uWebSockets.js" workflow
   - Provide the uWebSockets.js version tag (e.g., `v20.55.0`)
   - The workflow will create/update a release and build binaries for all platforms

2. **Pull Requests**: Automatically builds (without creating releases) to validate changes

### Build Process

The workflow consists of three jobs:

1. **ensure-release**: Creates or verifies the release exists (workflow_dispatch only)
2. **build-freebsd**: Builds FreeBSD binaries in a VM and uploads to the release
3. **build-linux**: Builds Linux binaries natively and uploads to the release

### Local Building

To build locally, clone the repository with submodules:

```bash
git clone --recursive https://github.com/louwers/uws-freebsd.git
cd uws-freebsd/uWebSockets.js
git checkout <version-tag>  # e.g., v20.55.0
git submodule update --init --recursive

# For FreeBSD
cd ..
patch -p0 < freebsd-build.patch
cd uWebSockets.js
make

# For Linux
cd uWebSockets.js
make
```

## License

Apache-2.0 (same as uWebSockets.js)
