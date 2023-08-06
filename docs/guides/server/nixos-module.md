# NixOS module
The `CC-YouCube/server` repository on GitHub provides a Nix flake, which includes a Nix package and a NixOS module.

## Nix package

!!! warning
    This method is not recommended for long-term setups; please use the NixOS module instead.

The server can be downloaded executed manually through `nix run github:CC-YouCube/server`. This is not recommended for long-term setups.

The Nix package provides a wrapped executable called `youcube-server` (in `/bin`) that should be executed instead of calling the module directly. This ensures that YouCube can find the correct Python modules and other executables.

## NixOS module

NixOS can be configured to start the server through the module in the flake.

First, add the YouCube server GitHub repository and Nixpkgs to your flake inputs (in `/etc/nixos/flake.nix`) and add it to the `nixosConfigurations.<your hostname>` set:

```nix
{
  inputs.nixpkgs.url = "github:NixOS/nixpkgs/release-23.05";
  inputs.youcube.url = "github:CC-YouCube/server";
  inputs.youcube.follows = "nixpkgs";

  nixosConfigurations.<your hostname> = nixpkgs.lib.nixosSystem {
    system = "x86_64-linux"; # FIXME: Set to your system architecture.
    modules = [
      youcube.services.youcube-server
      ./configuration.nix
    ];
  };
}
```

Now, add the following code to your `/etc/nixos/configuration.nix` (creating it if necessary:

```nix
{
  services.youcube-server = {
    enable = true;
  };
}
```

Rebuild your system with `sudo nixos-rebuild --flake`, then restart your server.

Check if the server is running with `systemctl`:

```shell
sudo systemctl status youcube-server
```

If all looks well, browse the [NixOS options](#nixos-options) section and configure to your heart's content.

## NixOS options

This is an exhaustive manual for the `youcube` NixOS module available in the `github:CC-YouCube/server` flake.

### `youcube.enable`

Enables the YouCube server. Currently, this adds a `systemd` unit to your current configuration.

### `youcube.host`

The host of the YouCube server.

### `youcube.port`

The port of the YouCube server. Defaults to `5000`.

### `youcube.packages.sanjuuni`

Override the package used for [Sanjuuni](https://sanjuuni.madefor.cc).

### `youcube.packages.ffmpeg`

Override the package used for [FFmpeg](https://ffmpeg.org).

### `youcube.spotify.credentialsFile`

File containing the `SPOTIFY_CLIENT_ID` and `SPOTIFY_CLIENT_SECRET` in the format of an `EnvironmentFile=`, as described by `systemd.exec(5)`. See [the Spotify support section](/guides/server/spotify-support/) for more information.

If this option is not set, Spotify support will be disabled.
