<h1 align="center">SourceKit-LSP Marketplace</h1>

<p align="center">
  A Claude Code plugin marketplace that adds Swift and Objective-C language server support through Apple's SourceKit-LSP.
</p>

<p align="center">
  <a href="https://github.com/tszaks/sourcekit-lsp-marketplace/actions/workflows/ci.yml"><img src="https://github.com/tszaks/sourcekit-lsp-marketplace/actions/workflows/ci.yml/badge.svg" alt="CI"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/tszaks/sourcekit-lsp-marketplace" alt="MIT license"></a>
  <img src="https://img.shields.io/badge/macOS-Xcode%20required-blue" alt="macOS with Xcode">
  <img src="https://img.shields.io/badge/Claude%20Code-2.0.65%2B-orange" alt="Claude Code 2.0.65 or later">
</p>

```text
/plugin
  Marketplaces > Add: tszaks/sourcekit-lsp-marketplace
  Discover > sourcekit-lsp > Install
```

This repository is a Claude Code marketplace with one plugin, `sourcekit-lsp`. The plugin tells Claude Code to start Apple's `sourcekit-lsp` server for Swift and Objective-C files, so Claude gets real symbol navigation and diagnostics instead of guessing from text search.

It is for people who build iOS and macOS apps with Claude Code on a Mac. The plugin is a small configuration file. It does not bundle or modify SourceKit-LSP: it runs the copy that ships with Xcode.

## Features

- **Jump to definition.** Navigate to symbol definitions.
- **Find references.** Find usages of a symbol across the codebase.
- **Code completion.** Completions from the Swift toolchain.
- **Real-time diagnostics.** Errors and warnings as the code changes.
- **Symbol search.** Search for symbols across the workspace.

These are the standard Language Server Protocol features that SourceKit-LSP provides. What Claude Code surfaces depends on your Claude Code version.

## Supported file types

| Extension | Language |
|---|---|
| `.swift` | Swift |
| `.m` | Objective-C |
| `.mm` | Objective-C++ |
| `.h` | C and Objective-C headers |

## Requirements

- macOS with Xcode installed. SourceKit-LSP ships with Xcode, and the plugin runs the `sourcekit-lsp` command from your `PATH`.
- Claude Code 2.0.65 or later.

Check that the server is available:

```sh
which sourcekit-lsp
sourcekit-lsp --help
```

## Install

1. Open Claude Code.
2. Run `/plugin`.
3. Go to the **Marketplaces** tab.
4. Add `tszaks/sourcekit-lsp-marketplace`.
5. Go to the **Discover** tab.
6. Select and install `sourcekit-lsp`.

Or from a terminal:

```sh
claude plugin marketplace add tszaks/sourcekit-lsp-marketplace
claude plugin install sourcekit-lsp@sourcekit-lsp-marketplace
```

## Usage

Once installed, Claude Code uses SourceKit-LSP when it works with Swift and Objective-C files. There is nothing to configure per project. SourceKit-LSP works best in a Swift package or an Xcode project that has been built at least once, because it reads the build index.

## Configuration

The server settings live in [sourcekit-lsp/.lsp.json](sourcekit-lsp/.lsp.json):

| Setting | Value |
|---|---|
| `command` | `sourcekit-lsp` |
| `transport` | `stdio` |
| `maxRestarts` | `3` |
| `.swift` | `swift` |
| `.m` | `objective-c` |
| `.mm` | `objective-cpp` |
| `.h` | `c` |

To use a different toolchain, put it first on your `PATH` or edit `command` in your own copy of the plugin.

## How it works

- Claude Code reads `.claude-plugin/marketplace.json` and finds the `sourcekit-lsp` plugin.
- The plugin's `.lsp.json` starts `sourcekit-lsp` over stdio for the file types above.
- Language intelligence comes from the Xcode toolchain already on your Mac.

## Using with agents

Paste this into an agent that has a shell:

```txt
Repo: tszaks/sourcekit-lsp-marketplace
Goal: Add Swift/Obj-C SourceKit-LSP support to Claude Code.
Setup:
1) Ensure macOS with Xcode installed (which sourcekit-lsp must print a path)
2) claude plugin marketplace add tszaks/sourcekit-lsp-marketplace
3) claude plugin install sourcekit-lsp@sourcekit-lsp-marketplace
Use:
- Work in .swift/.m/.mm/.h files with improved definitions/references/diagnostics
```

## FAQ

**Does it work on Linux or Windows?**
Not as written. The plugin expects `sourcekit-lsp` on your `PATH`. On Linux you can install a Swift toolchain that includes it, but this plugin is only tested with the one that ships with Xcode.

**Does it send my code anywhere?**
No. The plugin only starts a local program. SourceKit-LSP runs on your machine and talks to Claude Code over stdio.

**Which license applies?**
This repository is MIT. SourceKit-LSP itself is a separate project from Apple, licensed under Apache-2.0, and is not part of this repository.

## Contributing

Bug reports and pull requests are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) first. Security problems go through [SECURITY.md](SECURITY.md). Everyone taking part follows the [Code of Conduct](CODE_OF_CONDUCT.md).

Docs: [AGENTS.md](AGENTS.md) · [changelog](CHANGELOG.md)

## License

[MIT](LICENSE) © 2026 Tyler Szakacs. Made by [Szakacs Media](https://szakacsmedia.com).
