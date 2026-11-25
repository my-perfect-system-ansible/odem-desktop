---
namespace: odem
collection: desktop
role: lightdm
---

# `odem.desktop.lightdm`

Install X11 + WM packages, configure the lightdm greeter and per-user WM dotfiles

Merges the former `odem.desktop.x11` (X11 server + build deps) and
`odem.desktop.wm` (WM support packages + per-user picom/dunst dotfiles)
roles into the lightdm greeter role. Per-user parts are gated by the
`desktop_lightdm` user-role key (formerly `desktop_wm`).

## Default variables

| Variable | Default | Description |
|---|---|---|
| `lightdm_enable_wm` | `true` | Install window manager support packages and deploy the per-user picom/dunst dotfiles (former odem.desktop.wm) |
| `lightdm_enable_x11` | `true` | Install the X11 server + build dependency packages (former odem.desktop.x11) |
| `lightdm_greeter_conf` | `/etc/lightdm/lightdm-gtk-greeter.conf` | Path to the lightdm gtk greeter config file |
| `lightdm_packages_wm` | `[22 items]` | Window manager support packages (Debian defaults) |
| `lightdm_packages_x11` | `[11 items]` | X11 server + build dependency packages (Debian defaults) |
| `lightdm_wallpaper` | `wormhole.jpg` | Wallpaper filename (must be in lightdm_wallpapers_dir) |
| `lightdm_wallpapers_dir` | `/usr/share/images/desktop/wallpaper` | Directory containing wallpaper images (odem.desktop.essentials deploys this) |

## Dependencies

- `odem.os.user`

## Example usage

```yaml
- hosts: all
  roles:
    - odem.desktop.lightdm
```

## Role metadata

- **Min Ansible version**: `2.16.0`
- **License**: GPL-3.0-or-later
- **Platforms**: Debian (trixie), Fedora (45)
- **Tasks file lines**: 8

## Related files

- [`meta/main.yml`](meta/main.yml) — galaxy_info + role dependencies
- [`meta/argument_specs.yml`](meta/argument_specs.yml) — variable spec (the source of the variable table above)
- [`defaults/main.yml`](defaults/main.yml) — variable defaults (the source of the default values above)