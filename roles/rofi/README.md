---
namespace: odem
collection: desktop
role: rofi
---

# `odem.desktop.rofi`

Install rofi launcher + per-user config and 8 boot scripts

## Default variables

| Variable | Default | Description |
|---|---|---|
| `rofi_repo_dest` | `{{ user_default_repo_dir_mps }}/mps-desktop-rofi` | Destination path for the mps-desktop-rofi clone |
| `rofi_repo_url` | `https://github.com/my-perfect-system/mps-desktop-rofi.git` | mps-desktop-rofi git repository URL |
| `rofi_repo_version` | `main` | Branch or tag of the mps-desktop-rofi repository to deploy |
| `rofi_packages` | `- rofi` | Rofi packages |
| `rofi_scripts` | `[8 items]` | Per-user rofi boot scripts to deploy to ~/.local/bin/ |
| `rofi_themes` | `- rofi-boot-autorandr.rasi<br>- rofi-boot-dwmswitch.rasi<br>- rofi-boot-launcher.rasi<br>- rofi-boot-powermenu.rasi` | Rofi theme filenames to deploy to rofi_themes_dir |
| `rofi_themes_dir` | `/usr/share/rofi/themes` | System-wide rofi themes directory |

## Dependencies
- `odem.os.user`
- Configuration is cloned from the [mps-desktop-rofi](https://github.com/my-perfect-system/mps-desktop-rofi) git repository (`rofi_repo_url`); themes, per-user config, and scripts are deployed from that clone.

## Example usage

```yaml
- hosts: all
  roles:
    - odem.desktop.rofi
```

## Role metadata

- **Min Ansible version**: `2.16.0`
- **License**: GPL-3.0-or-later
- **Platforms**: Debian (trixie)
- **Tasks file lines**: 8

## Related files

- [`meta/main.yml`](meta/main.yml) — galaxy_info + role dependencies
- [`meta/argument_specs.yml`](meta/argument_specs.yml) — variable spec (the source of the variable table above)
- [`defaults/main.yml`](defaults/main.yml) — variable defaults (the source of the default values above)
