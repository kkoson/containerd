# containerd

[![Build Status](https://github.com/containerd/containerd/workflows/CI/badge.svg)](https://github.com/containerd/containerd/actions)
[![Go Report Card](https://goreportcard.com/badge/github.com/containerd/containerd)](https://goreportcard.com/report/github.com/containerd/containerd)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

An industry-standard container runtime with an emphasis on simplicity, robustness, and portability. This is a fork of [containerd/containerd](https://github.com/containerd/containerd).

## Overview

containerd is available as a daemon for Linux and Windows. It manages the complete container lifecycle of its host system: image transfer and storage, container execution and supervision, low-level storage and network attachments, etc.

## Getting Started

### Prerequisites

- Go 1.21 or later
- Linux kernel 4.x or later (for Linux)
- `runc` or another OCI-compliant runtime

### Development Environment

This project includes a [Dev Container](.devcontainer/) configuration for a consistent development environment.

1. Open this repository in VS Code
2. When prompted, click **Reopen in Container**
3. The environment will be set up automatically

### Building from Source

```bash
# Clone the repository
git clone https://github.com/containerd/containerd.git
cd containerd

# Build the binaries
make binaries

# Run tests
make test

# Run a specific test package (useful during development)
go test ./snapshots/... -v
```

### Installation

```bash
# Install containerd
make install
```

## Architecture

containerd is designed to be embedded into a larger system, rather than being used directly by developers or end-users. It exposes a gRPC API over a local UNIX socket.

Key components:

- **Client**: Go client library for interacting with the containerd daemon
- **Snapshotter**: Pluggable snapshotters for managing container filesystems
- **Content Store**: Content-addressable storage for images and other blobs
- **Runtime**: Pluggable runtimes (e.g., runc, kata-containers)
- **Metadata**: Bolt-backed metadata store

## Contributing

We welcome contributions! Please see our [contributing guidelines](CONTRIBUTING.md) for details.

### Reporting Issues

Please use the GitHub issue templates provided:
- [Bug Report](.github/ISSUE_TEMPLATE/bug_report.yaml)
- [Feature Request](.github/ISSUE_TEMPLATE/feature_request.yaml)
- [CRI KEP](.github/ISSUE_TEMPLATE/cri_kep.yaml)

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

This project is a fork of the original [containerd/containerd](https://github.com/containerd/containerd) project, maintained by the containerd authors and contributors.
