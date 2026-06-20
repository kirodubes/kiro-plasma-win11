<p align="center">
  <img src="kiro.jpg" alt="Kiro" width="220" />
</p>

# kiro-plasma-win11

Kiro's **Kiro Win11** Plasma global theme — a Windows 11 look for the Kiro Plasma edition,
packaged as ready-to-pick Global Themes.

Everything ships under a `Kiro-` namespace, so it **coexists with the upstream Win11OS
theme** — install the real `win11os-kde-theme-git` alongside it without any file conflict.

## What it ships

Global Themes you select in **System Settings → Appearance → Global Themes**:
**Kiro Win11 Light** and **Kiro Win11 Dark**, each with its full set of layers:

| Layer | Path | Notes |
|---------------------|------------------------------------------|------------------------------|
| Plasma desktop theme | `/usr/share/plasma/desktoptheme/Kiro-Win11-{light,dark}` | panels, widgets, popups |
| Global themes (look-and-feel) | `/usr/share/plasma/look-and-feel/com.kiroproject.Win11-{light,dark}` | the two variants |
| Window decorations | `/usr/share/aurorae/themes/Kiro-Win11-{light,dark}` | Aurorae titlebars |
| Color schemes | `/usr/share/color-schemes/Kiro-Win11{Light,Dark}.colors` | application colours |
| Kvantum themes | `/usr/share/Kvantum/Kiro-Win11-{light,dark}` | Qt app styling |
| Kvantum default selection | `/etc/xdg/Kvantum/kvantum.kvconfig` | system default (`Kiro-Win11-light`) |
| SDDM login themes | `/usr/share/sddm/themes/Kiro-Win11-{light,dark}` | the login screen (Qt6) |
| Cursors | `/usr/share/icons/kiro-win11-cursors` | bundled Windows-style cursors |

**Icons:** the Win11 icon set is **bundled** (built fresh from upstream at every package
build) and installed as **`kiro-win11`** to avoid conflicting with an AUR `win11-icon-theme`
package — no external icon dependency. Already Plasma-6 native.

## Install

```bash
sudo pacman -S kiro-plasma-win11
```

Then open **System Settings → Appearance → Global Themes** and apply **Kiro Win11 Light**
or **Kiro Win11 Dark**.

## Heritage

Based on [yeyushengfan258/Win11OS-kde](https://github.com/yeyushengfan258/Win11OS-kde),
[Win11-icon-theme](https://github.com/yeyushengfan258/Win11-icon-theme), and
[We10XOS-cursors](https://github.com/yeyushengfan258/We10XOS-cursors), GPL-3.0. See
[UPSTREAM.md](./UPSTREAM.md) for exact sources, the bundled-icon rename, and the
fixed upstream cursor reference.
