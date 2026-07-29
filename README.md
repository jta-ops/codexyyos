# CodexyyOS

A macOS-inspired Linux distro (elementary OS / Pantheon base) with the
Codexyy dark/cyan visual identity, built entirely via GitHub Actions.

No build artifacts are produced or stored on the authoring machine — every
ISO/qcow2 image is built by CI and published as a GitHub Release.

## Status

Phase 0 (discovery) complete. See `docs/phase-plan.md`.

## Brand tokens (source: codexyy.dev)

| Token | Value |
|---|---|
| bg | `#07070a` / `#0d0d12` / `#141420` |
| border | `#1a1a26` / `#252535` |
| accent | `#00d4ff` |
| accent-2 | `#4effa8` |
| purple | `#a78bfa` |
| orange | `#ff6b35` |
| text | `#e2e2ec` / `#7878a0` / `#3a3a52` |
| font-display | Syne |
| font-body | DM Sans |
| font-mono | JetBrains Mono |

## Architecture

Build runs on `ubuntu-latest` GitHub Actions runners:
1. `debootstrap`/`live-build` assembles an elementary OS (Ubuntu Noble +
   Pantheon) chroot.
2. Branding layer (theme, wallpapers, fonts, boot animation/sound) is
   overlaid.
3. `squashfs-tools` + `xorriso` produce a live ISO.
4. ISO is converted to a bootable, persistent `qcow2` for QEMU.
5. Artifact is attached to a GitHub Release, not committed to git.
