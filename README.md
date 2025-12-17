<p align="center">
  <img src="https://raw.githubusercontent.com/ApiliumCode/aingle/main/assets/aingle.svg" alt="AIngle Logo" width="200"/>
</p>

<h1 align="center">ainglenix</h1>

<p align="center">
  <strong>Nix development environment for AIngle</strong>
</p>

<p align="center">
  <a href="https://nixos.org/"><img src="https://img.shields.io/badge/Nix-5277C3?logo=nixos&logoColor=white" alt="Nix"/></a>
  <a href="https://github.com/ApiliumCode/ainglenix/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-blue.svg" alt="License"/></a>
  <a href="https://www.rust-lang.org/"><img src="https://img.shields.io/badge/rust-1.75+-orange.svg" alt="Rust"/></a>
</p>

---

## Overview

Reproducible development environment for AIngle using Nix. This provides a consistent, isolated build environment with all required dependencies for developing, building, and testing AIngle applications.

## Features

- **Reproducible builds** - Same environment on any machine
- **Multi-platform** - Linux (x86_64, aarch64) and macOS (Intel, Apple Silicon)
- **Complete toolchain** - Rust, Cargo, WASM tools, and all dependencies
- **Isolated** - No conflicts with system packages
- **Fast setup** - Single command to get started

## Requirements

- [Nix package manager](https://nixos.org/download.html)
- Nix flakes enabled (recommended)

### Enable Flakes

Add to `~/.config/nix/nix.conf`:

```
experimental-features = nix-command flakes
```

## Quick Start

```bash
# Enter the development shell
nix develop github:ApiliumCode/ainglenix

# Or clone and enter locally
git clone https://github.com/ApiliumCode/ainglenix.git
cd ainglenix
nix develop
```

## What's Included

| Tool | Version | Purpose |
|------|---------|---------|
| Rust | 1.75+ | Core language |
| Cargo | Latest | Package manager |
| wasm-pack | Latest | WASM compilation |
| Node.js | 18+ | JavaScript tooling |
| OpenSSL | Latest | Cryptography |
| pkg-config | Latest | Library discovery |

## Platform Support

| Platform | Architecture | Status |
|----------|--------------|--------|
| Linux | x86_64 | Supported |
| Linux | aarch64 | Supported |
| macOS | x86_64 (Intel) | Supported |
| macOS | aarch64 (Apple Silicon) | Supported |

## Usage with AIngle

```bash
# Clone AIngle
git clone https://github.com/ApiliumCode/aingle.git
cd aingle

# Enter development environment
nix develop github:ApiliumCode/ainglenix

# Build the project
cargo build --release

# Run tests
cargo test
```

## Customization

Create a `flake.nix` in your project:

```nix
{
  inputs = {
    ainglenix.url = "github:ApiliumCode/ainglenix";
  };

  outputs = { self, ainglenix }:
    ainglenix.lib.mkFlake {
      # Add your customizations here
    };
}
```

## Part of AIngle

This repository is part of the [AIngle](https://github.com/ApiliumCode/aingle) ecosystem - a Semantic DAG framework for IoT and distributed AI applications.

## License

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.

---

<p align="center">
  <sub>Maintained by <a href="https://apilium.com">Apilium Technologies</a> - Tallinn, Estonia</sub>
</p>
