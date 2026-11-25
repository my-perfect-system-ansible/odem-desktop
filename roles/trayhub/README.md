---
namespace: odem
collection: desktop
role: trayhub
---

# `odem.desktop.trayhub`

Deploy the mps-trayhub tray/launcher app per user

Clones [mps-desktop-trayhub](https://github.com/my-perfect-system/mps-desktop-trayhub)
into the system-wide mps repo dir, installs the PyQt6 runtime system-wide, and
runs the repo's `install.sh` per opted-in user (app to
`~/.local/share/mps-trayhub`, config + plugins to `~/.config/mps-trayhub`,
`mps-trayhub` command, autostart + app-menu entries, rofi wiring).

## Default variables

| Variable | Default | Description |
|---|---|---|
| `trayhub_enable_packages` | `true` | Install the PyQt6 runtime (python3-pyqt6) system-wide |
| `trayhub_enable_rofi` | `true` | Let the repo installer wire the rofi launcher/config/theme (MPS_TRAYHUB_ENABLE_ROFI) |
| `trayhub_packages` | `- python3-pyqt6` | PyQt6 runtime packages (same name on Debian and Fedora) |
| `trayhub_repo_dest` | `{{ user_default_repo_dir_mps }}/mps-desktop-trayhub` | Clone destination of our trayhub app repo |
| `trayhub_repo_url` | `https://github.com/my-perfect-system/mps-desktop-trayhub.git` | Git URL of our trayhub app repo |
| `trayhub_repo_version` | `main` | Git ref (tag/branch) of our trayhub app repo to clone |

## Dependencies

- `odem.os.user`

## Example usage

```yaml
- hosts: all
  roles:
    - odem.desktop.trayhub
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