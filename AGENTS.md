# SourceKit-LSP Marketplace

A Claude Code plugin marketplace with one plugin, `sourcekit-lsp`, which starts Apple's SourceKit-LSP for Swift and Objective-C files. The repository is JSON configuration and docs only. There is no program code.

## Check
- `claude plugin validate .` (needs Claude Code; one known warning: the marketplace has no description).
- `jq empty .claude-plugin/marketplace.json sourcekit-lsp/plugin.json sourcekit-lsp/.lsp.json` (this is what CI runs).
- `which sourcekit-lsp` should print a path on a Mac with Xcode.
- Do not run `claude plugin install` against the user's real Claude Code setup unless asked.

## File map
- `.claude-plugin/marketplace.json`: the marketplace manifest and the plugin list.
- `sourcekit-lsp/plugin.json`: plugin metadata.
- `sourcekit-lsp/.lsp.json`: the language server command, transport, and extension-to-language map.
- `README.md`, `SECURITY.md`, `CONTRIBUTING.md`, `CHANGELOG.md`: user-facing docs.

## Conventions
- Keep the plugin version identical in `marketplace.json` and `plugin.json`.
- Match the surrounding files: two-space JSON, same key order.
- The plugin must stay a plain `sourcekit-lsp` launch over stdio. Do not add arguments that fetch code or touch the network.
- `plugin.json` lists `Apache-2.0` as the license and `swiftlang/sourcekit-lsp` as the repository. That describes the upstream server, not this repo (MIT). Do not change it without asking the owner.
- Update `README.md` and `CHANGELOG.md` when file types, requirements or settings change.
