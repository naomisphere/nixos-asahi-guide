# Widevine Setup Guide
If you're trying to set up Widevine, you've probably stumbled upon marcan's [```widevine-installer```](https://github.com/AsahiLinux/widevine-installer/) script, and found out that although it reports successful when done, it doesn't work at all. Not after logging out, not after rebooting, and not after erasing your NixOS install and  reinstalling.

This can be fixed using a NixOS wrapper for the script. See the link below:
https://github.com/epetousis/nixos-aarch64-widevine

Here is a simple flake implementing the overlay, which I put in ```/etc/nixos```:
```
{
  description = "Widevine aarch64 NixOS overlay";

  inputs = {
    nixpkgs.url = "github:NixOS/nixpkgs/nixos-25.05";
    nixos-aarch64-widevine.url = "github:epetousis/nixos-aarch64-widevine";
  };

  outputs = { self, nixpkgs, nixos-aarch64-widevine, ... }:
    let
      system = "aarch64-linux";
      pkgs = import nixpkgs {
        inherit system;
        overlays = [ nixos-aarch64-widevine.overlays.default ];
      };
    in {
      nixosConfigurations.hostnameHere = nixpkgs.lib.nixosSystem {
        inherit system;
        modules = [
          ./configuration.nix
          {
            system.stateVersion = "25.05";
         }
      ];
        pkgs = pkgs;
      };
   };
}
```       

```cd``` into the flake directory and rebuild the machine from the flake. See: \
```man -P 'less -p "#name"' nixos-rebuild```
