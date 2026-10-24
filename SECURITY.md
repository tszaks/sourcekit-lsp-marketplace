# Security policy

## Supported versions

Only the latest version of the plugin gets fixes.

| Version | Supported |
|---|---|
| 0.1.x (latest) | Yes |
| Older | No |

## Reporting a vulnerability

Please report security problems privately, not in a public issue.

Use GitHub private vulnerability reporting: open the **Security** tab of this repository and choose **Report a vulnerability**. If that is not available to you, email tyler@szakacsmedia.com.

Please include what you found, what an attacker could do with it, and steps to reproduce.

You can expect a first reply within a few days. This repository is maintained by one person, so a fix may take longer, but you will get updates.

## What counts

This plugin makes Claude Code start a program on your computer. These areas matter most:

- **The command.** `sourcekit-lsp/.lsp.json` runs `sourcekit-lsp`, found through your `PATH`. Whatever program comes first on `PATH` under that name will run. Keep your `PATH` clean.
- **What the server can read.** SourceKit-LSP reads the source files and build index of the project you open. It can also run SwiftPM, which evaluates `Package.swift`, so opening an untrusted package can run that package's code. Treat an unknown Swift project like any other untrusted code.
- **Changes to the manifests.** Anything that makes the plugin run a different command, add arguments that fetch remote code, or contact the network is a vulnerability. Review changes to `.lsp.json` carefully.

The plugin itself makes no network requests and contains no code beyond JSON configuration.
