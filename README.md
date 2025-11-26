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
 ln -s /Volumes/My\ Shared\ Files/nix ~/nix
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

## First run

## Update run

## Recreate on a new machine

## Sources

- https://github.com/nix-darwin/nix-darwin
- https://github.com/zmre/mac-nix-simple-example
-
