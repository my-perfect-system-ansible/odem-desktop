# AGENTS.md — odem-desktop

Desktop GUI and window manager environment — qtile window manager, rofi /
thunar / trayhub helpers, kanata keyboard remapper, lightdm greeter +
X11 / window manager stacks, browser (firefox + brave), thunderbird,
spotify, grubmenu themes, per-user essentials incl. GNOME tools.

## Galaxy

- **namespace**: `odem`
- **name**: `desktop`
- **version**: `0.5.0`
- **dependencies**: `odem.os >=0.1.0`, `ansible.posix >=1.0.0`

## Roles

### Browser / system apps (single-package installs)

| Role | Description | Complexity |
|---|---|---|
| `odem.desktop.browser` | Firefox and Brave browsers (own toggle each). | 1 |
| `odem.desktop.thunderbird` | Thunderbird apt install. | 1 |
| `odem.desktop.spotify` | Spotify client (custom apt repo + signing key). | 1 |
| `odem.desktop.grubmenu` | GRUB theme + `/etc/default/grub` lineinfile + `update-grub`. | 1 |

### Window manager + helpers (per-user)

| Role | Description | Complexity |
|---|---|---|
| `odem.desktop.qtile` | Plain-file config repo clone (mps-desktop-qtile) + upstream qtile venv + system scripts. | 3 |
| `odem.desktop.kanata` | Per-user rustup / cargo install, udev rules, systemd user service, `enable-linger` loop. | 3 |
| `odem.desktop.essentials` | Per-user dotfile copy loops + `set_fact` builders + GNOME tools packages. | 2 |
| `odem.desktop.rofi` | Per-user dotfile + script copy loops (`product()` pairs). | 2 |
| `odem.desktop.thunar` | Per-user dotfile copy loop. | 2 |
| `odem.desktop.lightdm` | X11 + WM packages, greeter config, per-user picom/dunst dotfiles (former x11 + wm roles). | 2 |

## Conventions

- Browser / system app roles are single-package installs (apt + optional GPG key); kept as `install.yml` + `main.yml` 2-file roles.
- WM + helper roles are per-user; each has `facts.yml` (set_fact builders) + `install.yml` (system packages) + `configure.yml` (per-user copy loops). Multi-file by design.
- Per-user loops use `block:` with `loop: "{{ user_resolved | odem.os.odem_filter_users('desktop_<x>') }}"`.
