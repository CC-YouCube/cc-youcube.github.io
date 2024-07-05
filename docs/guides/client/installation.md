# Installation

The YouCube [client] can be installed by running one of the following commands:

=== "Pastebin"

    ```shell
    pastebin run swsmNAf7
    ```

=== "wget"

    ```shell
    wget run https://raw.githubusercontent.com/CC-YouCube/installer/main/src/installer.lua
    ```

## LevelOS / lStore

[![lStore Package]](https://github.com/CC-YouCube/client/actions/workflows/lstore-put.yml)

To install the YouCube client on [LevelOS], execute one of the following commands:

=== "By project name"

    ```shell
    lStore get YouCube <path>
    ```

=== "By project id"

    ```shell
    lStore get bpBYV1aG <path>
    ```

You can also use the StoreUI to install it.

![preview]

## UnicornPKG (Experimental)

The following command can be used to install the [client] using the [unicornpkg] package manager:

```shell
hoof install youcube
```

[unicornpkg]: https://unicornpkg.madefor.cc
[preview]: ../../assets/levelos.png
[LevelOS]: https://discord.com/invite/vBsjGqy99U
[client]: https://github.com/CC-YouCube/client
[lStore Package]: https://img.shields.io/github/actions/workflow/status/CC-YouCube/client/lstore-put.yml?branch=main&label=lStore%20Package&logo=github&style=for-the-badge
