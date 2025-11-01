# uws-freebsd

This repository contains a GitHub Actions workflow for building and releasing [uWebSockets.js](https://github.com/uNetworking/uWebSockets.js) on FreeBSD.

## Workflow

The workflow is located at `.github/workflows/build-and-release.yml` and performs the following steps:

1. **Checkout**: Clones this repository and the uWebSockets.js repository with all submodules
2. **Prepare build.c**: Prepends FreeBSD-specific defines to `build.c` to make it build as Linux
3. **Build in FreeBSD VM**: Uses `vmactions/freebsd-vm` to build inside a FreeBSD virtual machine
4. **Install Dependencies**: Installs CMake and LLVM 18 (Clang 18) in the FreeBSD VM
5. **Build**: Runs `make` to build the project, which produces `.node` binary files for different Node.js versions
6. **Release**: Creates a GitHub release with the built FreeBSD x64 `.node` files (only on tag pushes)

## FreeBSD Build Configuration

The FreeBSD build prepends two defines to `build.c`:
- `#define OS "freebsd"` - Sets the OS name for the output binaries
- `#define __linux 1` - Makes the build system use Linux build paths, which work on FreeBSD

## Triggering the Workflow

The workflow can be triggered in three ways:

1. **Tag Push**: Automatically runs when a tag matching the pattern `v*` is pushed (e.g., `v1.0.0`) - creates a release
2. **Pull Request**: Runs on pull requests for validation (build only, no release)
3. **Manual Dispatch**: Can be manually triggered from the GitHub Actions UI

## Built Artifacts

The workflow builds and releases the following FreeBSD files:
- `uws_freebsd_x64_115.node` (Node.js v20)
- `uws_freebsd_x64_127.node` (Node.js v22)
- `uws_freebsd_x64_137.node` (Node.js v24)
- `uws_freebsd_x64_141.node` (Node.js v25)

These files are included in the GitHub release for easy distribution.