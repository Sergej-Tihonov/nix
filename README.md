# Nix Darwin

## Simulation with UTM

Install UTM:

- https://mac.getutm.app/
- https://formulae.brew.sh/cask/utm#default

Install guest tools to enable clipboard sharing.

To simplify file editing, create a shared folder in UTM:

- Settings > Shared Folders > Add Folder
- Path: /Users/username/nix

Create a symlink to the shared folder:

```
ln -s /Volumes/My\ Shared\ Files/nix /etc/nix-darwin
```

## Installation

See: https://github.com/nix-darwin/nix-darwin?tab=readme-ov-file#prerequisites

```
curl -fsSL https://install.determinate.systems/nix | sh -s -- install --prefer-upstream-nix
```

To check the installed version

```
nix-shell -p nix-info
```

This will install and open nix shell.

Next run inside this shell:

```
nix-info -m
```

Example output:

```
 - system: `"aarch64-darwin"`
 - host os: `Darwin 25.1.0, macOS 26.1`
 - multi-user?: `yes`
 - sandbox: `no`
 - version: `nix-env (Nix) 2.32.4`
 - nixpkgs: `/nix/store/2f33dl1xv3wcw07qw3izsj3aw4ws9qch-source`
```

## Initial example

https://github.com/nix-darwin/nix-darwin/blob/master/modules/examples/flake/flake.nix

Identify LocalHostName and replace `"simple"` with it:
```
scutil --get LocalHostName
```

## First run

```
sergej@sergejs-Virtual-Machine nix % sudo nix run nix-darwin/master#darwin-rebuild -- switch --flake ~/nix/flake.nix
Password:
warning: $HOME ('/Users/sergej') is not owned by you, falling back to the one defined in the 'passwd' file ('/var/root')
building the system configuration...
warning: Path '/Users/sergej/nix/flake.nix' should point at the directory containing the 'flake.nix' file, not the file itself. Pretending that you meant '/Users/sergej/nix'
warning: creating lock file "/Users/sergej/nix/flake.lock":
```

You need to add `--flake ~/nix/flake.nix` as I don't use the `/etc/nix-darwin` directly.

Besides, it doesn't want to have the file but the folder with the file.


## Update run

```
sudo darwin-rebuild switch --flake ~/nix
```

## Recreate on a new machine

## Sources

- https://github.com/nix-darwin/nix-darwin
- https://github.com/zmre/mac-nix-simple-example
-

## Error handling
- https://github.com/nix-darwin/nix-darwin/issues/1360#issuecomment-2697423770
- https://github.com/nix-darwin/nix-darwin/issues/1330#issuecomment-2654133042
- https://github.com/NixOS/nix/issues/10202#issuecomment-2451952174

## Helpful commands

```
nix-shell -p git
```
