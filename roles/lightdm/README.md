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
| `lightdm_enable_service` | `true` | Enable + start the lightdm systemd service (Fedora ships no preset) and set `graphical.target` as the default boot target (molecule sets false — containers have no systemd) |
| `lightdm_enable_autologin` | `true` | Configure passwordless graphical autologin (group + PAM file + seat dropin) |
| `lightdm_autologin_user` | `""` | Autologin account — empty selects the first present user opted into `user_roles.desktop_lightdm` |
| `lightdm_autologin_session` | `qtile` | Session name (Name field of an /usr/share/xsessions .desktop file) |
| `lightdm_autologin_group` | `autologin` | Group gating passwordless autologin in the PAM file |
| `lightdm_autologin_pam` | `/etc/pam.d/lightdm-autologin` | Autologin PAM file (deployed on RedHat; Debian's package ships its own) |
| `lightdm_confd_dir` | `/etc/lightdm/lightdm.conf.d` | lightdm drop-in configuration directory |
| `lightdm_autologin_dropin` | `99-mps-autologin.conf` | Name of the autologin dropin |
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