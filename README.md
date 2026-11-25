# `odem.desktop` Ansible Collection

Desktop GUI and window manager environment — qtile window manager, rofi /
thunar / trayhub helpers, kanata keyboard remapper, lightdm greeter +
X11 / window manager stacks, browser (firefox + brave), thunderbird,
spotify, grubmenu themes, per-user essentials incl. GNOME tools.

## Galaxy metadata

- **namespace**: `odem`
- **name**: `desktop`
- **version**: `0.5.0`
- **dependencies**: `odem.os`, `ansible.posix`

See [`galaxy.yml`](galaxy.yml) for the canonical values.

## Roles

### Browser / system apps

| Role | Purpose |
|---|---|
| [`odem.desktop.browser`](roles/browser/README.md) | Firefox and Brave browsers (own toggle each). |
| [`odem.desktop.thunderbird`](roles/thunderbird/README.md) | Thunderbird apt install. |
| [`odem.desktop.spotify`](roles/spotify/README.md) | Spotify client (apt repo + signing key). |
| [`odem.desktop.grubmenu`](roles/grubmenu/README.md) | GRUB theme + `/etc/default/grub` + `update-grub`. |

### Window manager + helpers (per-user)

| Role | Purpose |
|---|---|
| [`odem.desktop.qtile`](roles/qtile/README.md) | Plain-file config from mps-desktop-qtile + upstream pip venv. |
| [`odem.desktop.kanata`](roles/kanata/README.md) | Per-user rustup install, udev rules, systemd user service. |
| [`odem.desktop.essentials`](roles/essentials/README.md) | Per-user dotfile copies + GNOME tools packages. |
| [`odem.desktop.rofi`](roles/rofi/README.md) | Per-user dotfile + script copies. |
| [`odem.desktop.thunar`](roles/thunar/README.md) | Per-user dotfile copies. |
| [`odem.desktop.lightdm`](roles/lightdm/README.md) | X11 + WM packages, greeter config, per-user picom/dunst dotfiles. |

## Installation

```bash
ansible-galaxy collection install odem.desktop
```

## Usage

```yaml
- hosts: desktops
  become: true
  vars:
    user_catalog:
      alice:
        user_roles:
          desktop_qtile: true
          desktop_kanata: true
  roles:
    - odem.os.user
    - odem.desktop.lightdm
    - odem.desktop.qtile
```

## Documentation

- [`AGENTS.md`](AGENTS.md) — developer conventions
- `roles/<role>/README.md` — per-role variable docs

## License

GPL-3.0-or-later
