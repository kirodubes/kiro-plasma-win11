# Upstream references — kiro-plasma-win11

Everything needed to refresh this theme from upstream in the future.

## Sources

| Component | Source | Notes |
|---------------------------|------------------------------------------|----------------------------|
| Theme (look-and-feel, desktoptheme, aurorae, color-schemes, Kvantum, SDDM) | `https://github.com/yeyushengfan258/Win11OS-kde` @ `9f021c3` | simple `cp` install, vendored from git |
| Icons | `https://github.com/yeyushengfan258/Win11-icon-theme` | **fetched + built at every package build** (PKGBUILD `git+` source), installed as `kiro-win11` |
| Cursors | `https://github.com/yeyushengfan258/We10XOS-cursors` | bundled `dist/` as `kiro-win11-cursors` |

- **Author:** yeyushengfan258 · **License:** GPL-3.0 (upstream `LICENSE` carried in).
- **Plasma 6:** the look-and-feel ships proper `metadata.json` (`KPackageStructure`,
  `X-Plasma-APIVersion 2`) — **no conversion needed**. The desktoptheme uses
  `metadata.desktop` (left as-is; Plasma 6 still loads Plasma styles from it, and it
  carries `[AdaptiveTransparency]`/`[ContrastEffect]` hints). SDDM `6.0` (`QtVersion=6`).

## What was copied (source → install path)

From `yeyushengfan258/Win11OS-kde`:
| Source | Installed to |
|------------------------------|----------------------------------------|
| `plasma/look-and-feel/com.github.yeyushengfan258.Win11OS-{dark,light}` | `usr/share/plasma/look-and-feel/` |
| `plasma/desktoptheme/Win11OS-{dark,light}` | `usr/share/plasma/desktoptheme/` |
| `aurorae/Win11OS-{dark,light}` | `usr/share/aurorae/themes/` |
| `color-schemes/*.colors`, `Kvantum/Win11OS-{dark,light}` | `usr/share/{color-schemes,Kvantum}/` |
| `sddm-{dark,light}/6.0/*` | `usr/share/sddm/themes/` (drop the stray `install.sh`) |

Icons: PKGBUILD runs `Win11-icon-theme/install.sh -n kiro-win11 -d <pkgdir>/usr/share/icons`.
Cursors: `We10XOS-cursors/dist` → `usr/share/icons/kiro-win11-cursors`.

## Kiro edits to re-apply after any refresh

1. **Icon rename.** Both look-and-feel `defaults` reference `Theme=Win11` upstream → set to
   `Theme=kiro-win11` (the bundled, renamed icon theme; avoids the AUR `win11-icon-theme`
   file conflict).
2. **Upstream cursor bug.** Upstream `defaults` reference `Win10OS-cursors` (dark) and a
   stray `ArcDusk-cursors` (light, wrong leftover) → set both to `cursorTheme=kiro-win11-cursors`
   (the bundled cursor).
3. Drop the `install.sh` that `sddm-*/6.0/*` copies into `sddm/themes/`.

Kiro-only file (not upstream — leave as is on refresh):
- `etc/xdg/Kvantum/kvantum.kvconfig` → `[General] theme=Win11OS-light` (system XDG default
  layer, read by Kvantum for every user; mirrors kiro-plasma-nord).

## Verify on the Plasma test box
Confirm both Win11OS variants appear and apply in System Settings → Global Themes, with the
`kiro-win11` icons + `kiro-win11-cursors` + Kvantum active.
