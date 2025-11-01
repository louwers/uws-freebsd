# uws-freebsd

This repository contains a GitHub Actions workflow for building and releasing [uWebSockets.js](https://github.com/uNetworking/uWebSockets.js).

## Workflow

The workflow is located at `.github/workflows/build-and-release.yml` and performs the following steps:

1. **Checkout**: Clones the uWebSockets.js repository with all submodules
2. **Install Dependencies**: Installs build tools including Clang 18, CMake, and other required packages
3. **Build**: Runs `make` to build the project, which produces `.node` binary files for different Node.js versions
4. **Release**: Creates a GitHub release with the built Linux x64 `.node` files

## Triggering the Workflow

The workflow can be triggered in two ways:

1. **Tag Push**: Automatically runs when a tag matching the pattern `v*` is pushed (e.g., `v1.0.0`)
2. **Manual Dispatch**: Can be manually triggered from the GitHub Actions UI

## Built Artifacts

The workflow builds and releases the following files:
- `uws_linux_x64_115.node` (Node.js v20)
- `uws_linux_x64_127.node` (Node.js v22)
- `uws_linux_x64_137.node` (Node.js v24)
- `uws_linux_x64_141.node` (Node.js v25)

These files are included in the GitHub release for easy distribution.