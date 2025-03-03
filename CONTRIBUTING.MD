 # Contributing to OpenTelemetry-eBPF Build Tools

## Introduction

Welcome to the OpenTelemetry-eBPF Build Tools repository! 🎉
This repository contains third-party tools and libraries needed to build projects in the `opentelemetry-ebpf` repository.

Building this repository results in a build environment container image that is then used for building artifacts of the main project (see the [Developer Guide](https://github.com/open-telemetry/opentelemetry-network/blob/main/docs/developing.md)).

We value all contributions, whether big or small, and encourage you to join us in improving this project. If you have questions, don’t hesitate to reach out to the OpenTelemetry community—we’re here to help!

### MacOS Prerequisites

To work with this repository on MacOS, you need:

**The [Homebrew](https://brew.sh/) package manager** (Ensure you have it installed)
[**Docker Desktop**](https://docs.docker.com/desktop/setup/install/mac-install/) (For containerized builds)
**CMake**: Install using Homebrew
  ```sh
  brew install cmake
  ```
**Make**: Installed along with developer tools; if Homebrew is working, you should have `make` available.

## Workflow

1. Fork the repository
2. Work on own branch
3. Create a PR to fix an issue

## Local Run/Build

### How to set up and run the project locally
Check out this repository.
Run the build script:
  ```sh
  ./build.sh
  ```

## Contribution Guidelines
Use clear and concise naming conventions for variables, functions, and files.

### Community Standards and Style Guides

This project adheres to the OpenTelemetry community's standards. Please ensure you:

Follow the [Code of Conduct](https://github.com/open-telemetry/community/blob/main/code-of-conduct.md).

Thank you for contributing to OpenTelemetry-eBPF Build Tools! 🎉
