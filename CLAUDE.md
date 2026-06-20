# kiro-plasma-win11 — Project Claude Instructions

## Overview
The **Windows 11** look Plasma global theme for the Kiro Plasma edition. Ships Win11OS
Light + Win11OS Dark as Global Themes. Sibling to [[kiro-plasma-sweet]],
[[kiro-plasma-nord]], [[kiro-plasma-layan]], [[kiro-plasma-whitesur]].

## Current state
- Source repo: `~/KIRO/kiro-plasma-win11` (payload `usr/`, Kvantum default `etc/xdg`).
- Build recipe: `~/KIRO-PKG-BUILD-APPS/kiro-plasma-win11`.
- Upstreams: yeyushengfan258/Win11OS-kde + Win11-icon-theme + We10XOS-cursors. See [UPSTREAM.md](./UPSTREAM.md).

## Patterns / things to know
- **Plasma 6 native** — look-and-feel ships `metadata.json` (no conversion, unlike Nord).
  Desktoptheme keeps `metadata.desktop` (Plasma 6 loads Plasma styles from it; do NOT
  convert — it carries `[AdaptiveTransparency]`/`[ContrastEffect]` hints that don't map to JSON).
- **Icons bundled + renamed (like kiro-plasma-whitesur).** `win11-icon-theme` is AUR-only,
  so the PKGBUILD fetches `Win11-icon-theme` as a second `git+` source and builds it at
  package time via `install.sh -n kiro-win11`. Installed as `kiro-win11` (+`-dark`). The 2
  look-and-feel `defaults` were repointed `Win11`→`kiro-win11`. Re-fetched every build.
- **Upstream cursor bug fixed:** defaults referenced `Win10OS-cursors` (dark) and a stray
  `ArcDusk-cursors` (light); both set to bundled `kiro-win11-cursors` (from We10XOS-cursors).
- **Cursor is bundled static** (`usr/share/icons/kiro-win11-cursors`), unlike the icons.
- **Drop the stray `install.sh`** that `sddm-*/6.0/*` copies into `sddm/themes/` on refresh.
- Kvantum default → `/etc/xdg/Kvantum/kvantum.kvconfig` (`Win11OS-light`), the system XDG
  layer (mirrors kiro-plasma-nord; better than /etc/skel — applies to all users incl. live ISO).
- Mixed delivery: payload → `/usr/share`, Kvantum selection → `/etc/xdg`. PKGBUILD copies both.
- **Test on the Plasma test box** — confirm both variants apply with kiro-win11 icons/cursors.
