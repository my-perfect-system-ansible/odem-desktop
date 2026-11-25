---
namespace: odem
collection: desktop
role: browser
---

# `odem.desktop.browser`

Install Firefox and Brave browsers

Merges the former `odem.desktop.firefox` (ESR/apt) and `odem.desktop.brave`
(HTTPS apt repo + signing key) roles; each browser is gated by its own
toggle.

## Default variables

| Variable | Default | Description |
|---|---|---|
| `browser_brave_apt_filename` | `brave-browser` | Filename for the Brave APT source list |
| `browser_brave_keyring_path` | `/usr/share/keyrings/brave-browser-archive-keyring.gpg` | Path to the Brave GPG keyring |
| `browser_brave_packages` | `- ca-certificates<br>- curl<br>- gnupg<br>- apt-transport-https` | Packages required to install Brave (prereqs, Debian only) |
| `browser_brave_repo_url` | `https://brave-browser-apt-release.s3.brave.com/` | Base URL for the Brave APT repository and key |
| `browser_enable_brave` | `true` | Install Brave via its HTTPS apt repository (Debian only) |
| `browser_enable_firefox` | `true` | Install Firefox (firefox-esr on Debian, firefox on Fedora) |

## Dependencies

- none (system-level installs)

## Example usage

```yaml
- hosts: all
  roles:
    - odem.desktop.browser
```

## Role metadata

- **Min Ansible version**: `2.16.0`
- **License**: GPL-3.0-or-later
- **Platforms**: Debian (trixie), Fedora (45)
- **Tasks file lines**: 3

## Related files

- [`meta/main.yml`](meta/main.yml) — galaxy_info + role dependencies
- [`meta/argument_specs.yml`](meta/argument_specs.yml) — variable spec (the source of the variable table above)
- [`defaults/main.yml`](defaults/main.yml) — variable defaults (the source of the default values above)