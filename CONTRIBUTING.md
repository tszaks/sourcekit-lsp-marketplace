# Contributing to SourceKit-LSP Marketplace

Thanks for helping. This repository is a Claude Code marketplace with one small plugin. The bar for changes is: does it keep the plugin simple, and does it work with the SourceKit-LSP that ships with Xcode?

By taking part you agree to follow the [Code of Conduct](CODE_OF_CONDUCT.md).

## Before you start

- For bugs, open an issue with the template.
- For features, open an issue first and describe the problem you want to solve.
- Small fixes (typos, clear bugs) can go straight to a pull request.
- Security problems go through [SECURITY.md](SECURITY.md), not a public issue.

## Setup

You need a Mac with Xcode and Claude Code. There is no build step.

```sh
git clone https://github.com/tszaks/sourcekit-lsp-marketplace.git
cd sourcekit-lsp-marketplace
```

Try your copy in Claude Code with `/plugin`, then add the marketplace from the local path.

## Checks

```sh
claude plugin validate .
jq empty .claude-plugin/marketplace.json sourcekit-lsp/plugin.json sourcekit-lsp/.lsp.json
```

CI runs the JSON check. `claude plugin validate .` needs Claude Code installed, so run it locally.

## Code style

- **Match the surrounding files.** Same key order and two-space JSON indentation.
- Keep versions in step: the plugin version in `.claude-plugin/marketplace.json` and `sourcekit-lsp/plugin.json` must match.
- Comments in docs explain *why*, not *what*.

## Pull request checklist

- [ ] `claude plugin validate .` and the `jq` check pass.
- [ ] The change is small and focused.
- [ ] Versions match in both manifests if you changed one.
- [ ] README updated if file types, requirements or settings changed.
- [ ] A line added under `[Unreleased]` in [CHANGELOG.md](CHANGELOG.md) for anything a user would notice.

## Using AI agents to contribute

Fine, as long as you read and understand what you submit and the checklist above is true. [AGENTS.md](AGENTS.md) tells coding agents how this repository works.

## License

By contributing you agree that your contribution is licensed under the [MIT License](LICENSE).
