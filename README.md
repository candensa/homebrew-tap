# Candensa Homebrew Tap

Official Homebrew tap for the [Candensa](https://candensa.sh) CLI.

Candensa is a self-hosted PaaS, internal developer platform, and cloud control plane. One command, any infrastructure: **deploy anything, on any infrastructure, from one control plane.**

This repository hosts the Homebrew formula for the `candensa` CLI. The formula is regenerated automatically on every Candensa release, so it always tracks the latest published version.

---

## Install

```sh
brew install candensa/tap/candensa
```

The first invocation taps this repo (`brew tap candensa/tap`) and installs the latest `candensa` release. After install:

```sh
candensa --version
```

Supported platforms: macOS (Intel + Apple Silicon) and Linux (amd64 + arm64).

---

## Quick start

Once installed, the most common loop is:

```sh
# log in to your control plane
candensa auth login --server https://control.your-domain.com

# deploy the current directory as a service
candensa deploy .

# tail logs while it rolls out
candensa logs --follow

# roll back if something looks wrong
candensa rollback <service>
```

Useful commands for operators running their own Candensa control plane or fleet:

```sh
candensa machines list             # show registered fleet machines
candensa server status             # control-plane health summary
candensa agent status              # agent-side runtime health
candensa dev tunnel                # local-dev tunnel to your control plane
```

All commands accept `--json` for stable, scriptable output:

```sh
candensa machines list --json | jq '.[] | select(.state == "active") | .id'
```

Run `candensa --help` for the full command tree, or `candensa <command> --help` for a specific one.

---

## Update

```sh
brew update
brew upgrade candensa
```

To see what version Homebrew would install without committing to the upgrade:

```sh
brew info candensa/tap/candensa
```

---

## Uninstall

```sh
brew uninstall candensa
brew untap candensa/tap
```

---

## What's in this repo

- `Formula/candensa.rb` — Homebrew formula for the `candensa` CLI. **Auto-generated; do not edit by hand.** Manual changes will be overwritten on the next Candensa release.
- `README.md` — this file.

The formula pins each platform binary by SHA-256.

---

## Security

Every Candensa release is signed with [Sigstore Cosign](https://github.com/sigstore/cosign) using keyless GitHub OIDC. Each release also ships an SPDX SBOM per artifact. Homebrew enforces the SHA-256 pin recorded in `Formula/candensa.rb` at install time, so a tampered binary would fail verification before extraction.

---

## Support

For documentation, support, and to report issues, visit [candensa.sh](https://candensa.sh).

---
