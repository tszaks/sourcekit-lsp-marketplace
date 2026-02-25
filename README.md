# SourceKit-LSP Plugin for Claude Code

A Claude Code marketplace plugin that provides Swift and Objective-C language server support via Apple's SourceKit-LSP.

## Features

- **Jump to Definition** - Navigate to symbol definitions instantly
- **Find References** - Find all usages of a symbol across your codebase
- **Code Completion** - Get intelligent completions as you type
- **Real-time Diagnostics** - See errors and warnings as you code
- **Symbol Search** - Search for symbols across your workspace

## Supported File Types

- `.swift` - Swift
- `.m` - Objective-C
- `.mm` - Objective-C++
- `.h` - C/Objective-C headers

## Requirements

- macOS with Xcode installed (SourceKit-LSP ships with Xcode)
- Claude Code 2.0.65+

## Installation

1. Open Claude Code
2. Run `/plugin`
3. Go to **Marketplaces** tab
4. Add: `tjzaks/sourcekit-lsp-marketplace`
5. Go to **Discover** tab
6. Select and install `sourcekit-lsp`

## Usage

Once installed, Claude Code will automatically use SourceKit-LSP when working with Swift files, enabling faster and more accurate code navigation.

## Author

Tyler Szakacs - [Szakacs Media Company](https://szakacsmedia.com)

## Quickstart TL;DR

1. Open Claude Code
2. Run `/plugin`
3. Add marketplace: `tszaks/sourcekit-lsp-marketplace`
4. Install `sourcekit-lsp` plugin from Discover

## How It Works (TL;DR)

- Plugin connects Claude Code to Apple's SourceKit-LSP on macOS
- Swift/Objective-C language intelligence is routed through SourceKit-LSP
- Claude tooling gets stronger symbol navigation and diagnostics support

## LLM Quick Copy

Use the copy button on this code block in GitHub.

```txt
Repo: sourcekit-lsp-marketplace
Goal: Add Swift/Obj-C SourceKit-LSP support to Claude Code.
Setup:
1) Ensure macOS with Xcode installed
2) In Claude Code run /plugin
3) Add marketplace tszaks/sourcekit-lsp-marketplace
4) Install sourcekit-lsp plugin
Use:
- Work in .swift/.m/.mm/.h files with improved definitions/references/diagnostics
How it works:
- Claude plugin -> SourceKit-LSP bridge -> language intelligence from Xcode toolchain
```
