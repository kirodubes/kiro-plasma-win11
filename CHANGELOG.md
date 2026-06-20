# Changelog

## 2026.06.20 — rename theme identity to Kiro namespace (coexist with upstream Win11OS)

### What Changed
- Renamed every shipped theme identity from the upstream `Win11OS` name into a `Kiro-Win11`
  namespace so the package **coexists with the upstream Win11OS theme** — a user can install
  `win11os-kde-theme-git` alongside this without any pacman file conflict — and so System
  Settings shows honest **Kiro Win11 Light** / **Kiro Win11 Dark** labels.

### Technical Details
- Look-and-feel `com.github.yeyushengfan258.Win11OS-{light,dark}` →
  `com.kiroproject.Win11-{light,dark}` (both `metadata.json` and legacy `metadata.desktop`).
  Desktoptheme, aurorae (+ `*rc`), Kvantum (+ inner `.kvconfig`/`.svg`), SDDM, and color
  schemes (`Win11OS{Light,Dark}` → `Kiro-Win11{Light,Dark}`) all renamed to `Kiro-Win11*`.
- SDDM `Main.qml` absolute self-paths repointed to the renamed dirs.
- Cross-references repointed: look-and-feel `defaults` (`ColorScheme`/`__aurorae__svg__`/
  `plasmarc name`) and `etc/xdg` Kvantum `theme=Kiro-Win11-light`. The bundled icon theme
  (`kiro-win11`) and cursor (`kiro-win11-cursors`) were already Kiro-named — unchanged.
- PKGBUILD: dropped `conflicts=(win11os-kde-theme-git)` and bumped `pkgrel`. The
  `install.sh -n kiro-win11` icon-build step is unchanged.

### Files Modified
- Renamed all theme dirs/files under `usr/share/{plasma,aurorae,color-schemes,Kvantum,sddm}` to `Kiro-Win11*`
- Look-and-feel `contents/defaults`, SDDM `Main.qml`, `etc/xdg/Kvantum/kvantum.kvconfig` — repointed
- `README.md`, `CLAUDE.md` — Kiro Win11 naming + coexistence note
- `../KIRO-PKG-BUILD-APPS/kiro-plasma-win11/PKGBUILD` — drop upstream conflicts, bump pkgrel

## 2026.06.20 — initial package

### What Changed
- New repo: **kiro-plasma-win11**, a **Windows 11** look Plasma global theme for the Kiro
  Plasma edition (Win11OS was a top-downloaded global theme on the KDE Store). Ships
  **Win11OS Light** and **Win11OS Dark** as full Global Themes.
- Combined the layers: 2 desktopthemes + 2 look-and-feel + 2 Aurorae + 2 color schemes +
  Kvantum (light/dark) + 2 SDDM themes (Qt6).
- **Already Plasma-6 native** — the look-and-feel ships proper `metadata.json`
  (`X-Plasma-APIVersion 2`); no conversion needed. Desktoptheme keeps its `metadata.desktop`
  (Plasma 6 still loads Plasma styles from it; carries AdaptiveTransparency hints).
- **Icons bundled, renamed:** the Win11 icon set is fetched fresh from upstream on every
  build (PKGBUILD `git+` source) and installed as **`kiro-win11`** (avoids the AUR
  `win11-icon-theme` file conflict). Both look-and-feel `defaults` repointed `Win11`→`kiro-win11`.
- **Fixed upstream cursor bug:** defaults referenced `Win10OS-cursors` (dark) and a stray
  `ArcDusk-cursors` (light) → both set to bundled **`kiro-win11-cursors`** (from We10XOS-cursors).
- **Default Kvantum selection** via `/etc/xdg/Kvantum/kvantum.kvconfig` (`Win11OS-light`).

### Technical Details
- Sources: [yeyushengfan258/Win11OS-kde](https://github.com/yeyushengfan258/Win11OS-kde)
  `9f021c3` (theme), [Win11-icon-theme](https://github.com/yeyushengfan258/Win11-icon-theme)
  (icons, built at package time), [We10XOS-cursors](https://github.com/yeyushengfan258/We10XOS-cursors)
  (cursors). Full mapping in [UPSTREAM.md](./UPSTREAM.md).
- License: GPL-3.0.
- Recipe depends on `kvantum`, `sddm`; makedepends `git`, `gtk-update-icon-cache`; copies `usr/` + `etc/`.

### Files Modified
- usr/share/plasma/look-and-feel/com.github.yeyushengfan258.Win11OS-{dark,light} (new)
- usr/share/plasma/desktoptheme/Win11OS-{dark,light} (new)
- usr/share/aurorae/themes/Win11OS-{dark,light}, color-schemes/Win11OS*.colors (new)
- usr/share/Kvantum/Win11OS-{dark,light}, sddm/themes/Win11OS-{dark,light} (new)
- usr/share/icons/kiro-win11-cursors (new); kiro-win11 icons built at package time
- etc/xdg/Kvantum/kvantum.kvconfig (new)
- README.md, CHANGELOG.md, CLAUDE.md, UPSTREAM.md, LICENSE, up.sh, setup.sh, kiro.jpg, .gitignore (new)
