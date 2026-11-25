---
namespace: odem
collection: desktop
role: thunar
---

# `odem.desktop.thunar`

Install thunar + plugins and per-user dotfiles

## Default variables

| Variable | Default | Description |
|---|---|---|
| `thunar_repo_dest` | `{{ user_default_repo_dir_mps }}/mps-desktop-thunar` | Destination path for the cloned mps-desktop-thunar repository |
| `thunar_repo_url` | `https://github.com/my-perfect-system/mps-desktop-thunar.git` | Git repository shipping thunar configuration |
| `thunar_repo_version` | `main` | Branch or tag of the mps-desktop-thunar repository to use |
| `thunar_packages` | `[6 items]` | Thunar core + plugin packages |
| `thunar_xfce_packages` | `- xfce4-goodies<br>- xfce4-places-plugin<br>- thunar-font-manager` | XFCE4 packages used by thunar |

## Dependencies

- `odem.os.user`
- The per-user Thunar and xfce4 configuration ships from the [mps-desktop-thunar](https://github.com/my-perfect-system/mps-desktop-thunar) repository, cloned at runtime via `thunar_repo_url`.

## Example usage

```yaml
- hosts: all
  roles:
    - odem.desktop.thunar
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
