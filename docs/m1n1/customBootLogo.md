# Custom boot logo

**Required Software:** [`imagemagick`](https://search.nixos.org/packages?channel=25.05&show=imagemagick&query=imagemagick)

When booting up your Mac to Asahi Linux, you see three logos, those being:
- Apple logo (iBoot1)
- Asahi Linux logo (m1n1 stage 1)
- Asahi Linux logo -again- (m1n1 stage 2)

This is because, by default, [```m1n1```](https://github.com/AsahiLinux/m1n1) stage 2 (which takes care of the third logo) uses the same logo as stage 1 (Asahi's). In the specific case of NixOS, this can be easily overriden by specifying a custom logo using the ```boot.m1n1CustomLogo``` argument. Keep in mind, the given logo must be a 256x256 PNG image.

e.g.
```
   boot = {
     loader.systemd-boot.enable = true;
     loader.efi.canTouchEfiVariables = false;
     m1n1CustomLogo = "/var/lib/nixos/NixOS_logo_256.png"
};
```

Upon running ```nixos-rebuild```, m1n1 will be rebuilt to use the given logo.
