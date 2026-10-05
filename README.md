# Hyprland

A NixOS configuration module that enables the [Hyprland](https://hyprland.org/)
Wayland compositor together with a login manager and a minimal desktop set.

## What it does

Importing `hyprland.nix` into your NixOS configuration:

- enables `programs.hyprland`, using the Hyprland package from the `hyprland`
  flake input,
- adds the Hyprland Cachix binary cache
  (`https://hyprland.cachix.org`) so you don't have to build Hyprland from
  source,
- sets up `greetd` with `tuigreet` as the login manager, launching Hyprland on
  login,
- installs a basic Wayland desktop toolkit: `hyprpaper` (wallpaper), `kitty`
  (terminal), `rofi-wayland` (launcher), `waybar` (status bar) and
  `gnome-icon-theme`.

## Requirements

This module expects a `hyprland` flake input to be available in your
configuration, for example:

```nix
inputs.hyprland.url = "github:hyprwm/Hyprland";
```

## Usage

Import `hyprland.nix` from your host configuration and make sure the flake
inputs are passed through (via `specialArgs`/`extraSpecialArgs`):

```nix
{
  imports = [
    ./hyprland.nix
  ];
}
```

Then rebuild:

```sh
sudo nixos-rebuild switch --flake .#myhost
```

## License

Released under the [MIT License](LICENSE).
