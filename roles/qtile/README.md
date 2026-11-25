---
namespace: odem
collection: desktop
role: qtile
---

# `odem.desktop.qtile`

Install qtile + per-user config copied from the mps-desktop-qtile repo

All former template variables (wallpapers, scratchpad dropdowns, VPN hosts,
kanata state path, autostart displays/keyboard, screenlayout command) moved
to the repo's `config/qtile/settings.py` — the single config spot. This role
copies plain files; it renders no templates.

## Default variables

| Variable | Default | Description |
|---|---|---|
| `qtile_config_repo_dest` | `{{ user_default_repo_dir_mps }}/mps-desktop-qtile` | Clone destination of our qtile config repo |
| `qtile_config_repo_url` | `https://github.com/my-perfect-system/mps-desktop-qtile.git` | Git URL of our qtile config repo (config + xsession + scripts) |
| `qtile_config_repo_version` | `main` | Git ref (tag/branch) of our qtile config repo to clone |
| `qtile_local_bin_dir` | `/usr/local/bin` | System-wide bin dir for qtile scripts |
| `qtile_local_bin_scripts` | `- qtile-startup.bash<br>- qtile-reload.bash<br>- qtile-restart.bash` | Qtile scripts to deploy to /usr/local/bin/ |
| `qtile_packages` | `[9 items]` | Qtile system dependencies |
| `qtile_repo_dest` | `~/venvs/qtile/src` | Per-user path to clone the qtile repo (use ~ for home dir) |
| `qtile_repo_url` | `https://github.com/qtile/qtile` | Git URL of the qtile repository |
| `qtile_repo_version` | `v0.31.0` | Git ref (tag/branch) of the qtile repository to clone |
| `qtile_user_scripts` | `- qtile-autostart-start.bash<br>- qtile-autostart-stop.bash` | Qtile scripts to deploy to ~/.local/bin/ (per-user) |
| `qtile_venv_path` | `~/.venvs/qtile` | Python venv path for qtile (avoids collision with odem.terminal.python) |
| `qtile_xsessions_dir` | `/usr/share/xsessions` | Xsession .desktop file directory |
| `qtile_xsessions_file` | `qtile.desktop` | Xsession .desktop file name |
| `qtile_xsessions_path` | `{{ qtile_xsessions_dir }}/{{ qtile_xsessions_file }}` | Full destination path for the xsession .desktop file (derived from dir+file) |

## Dependencies

- `odem.os.user`

## Example usage

```yaml
- hosts: all
  roles:
    - odem.desktop.qtile
```

## Role metadata

- **Min Ansible version**: `2.16.0`
- **License**: GPL-3.0-or-later
- **Platforms**: Debian (trixie), Fedora (45)
- **Tasks file lines**: 6

## Related files

- [`meta/main.yml`](meta/main.yml) — galaxy_info + role dependencies
- [`meta/argument_specs.yml`](meta/argument_specs.yml) — variable spec (the source of the variable table above)
- [`defaults/main.yml`](defaults/main.yml) — variable defaults (the source of the default values above)