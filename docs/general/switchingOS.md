# Switching between Asahi Linux and macOS

**Required Software:** [```asahi-bless```](https://search.nixos.org/packages?channel=25.05&show=asahi-bless&query=asahi-bless)\
**Recommended Software:** [KDE Plasma](https://nixos.wiki/wiki/KDE)

If you want to make your life easier by not having to hold the Power button to boot into macOS again while having NixOS as your startup disk, then ```asahi-bless``` is the answer.

Made by [WhatAmISupposedToDoHere](https://github.com/WhatAmISupposedToPutHere) (I don't know, either!), it is essentially a ```bless``` command but for Asahi Linux, that allows you to set the boot volume with a variety of choices. It is as simple as running:
```bash
sudo asahi-bless
```

This should do for the most part, however, if you want more precision, here's what you can do (```sudo asahi-bless --help```):

```bash
Usage: asahi-bless [OPTIONS]

Options:
  -n, --next                      Set boot volume for next boot only
  -l, --list-volumes              List boot volume candidates
      --set-boot <name_or_index>  Set boot volume by name or index
      --set-boot-macos            Set boot volume to macOS if unambiguous
  -y, --yes                       Do not ask for confirmation
      --get-boot                  Get currently selected boot target. May be combined with --next to show the next boot target.
      --clear-next                Clear the selected next boot target
  -h, --help                      Print help
  -V, --version                   Print version
  ```

## Now, let's... make a KDE Plasma application!

On KDE Plasma:
- Right click Kickoff (Application Launcher) > Edit Applications
- Click on a category of your choice (I recommend Utilities, it doesn't matter anyway)
- Click 'New Item', name it 'Reboot to macOS', or whatever you may prefer
- On the 'Program:' field, enter:
```bash
/bin/sh -c 'sudo asahi-bless -n -y --set-boot-macos && reboot'
```
- Go to the 'Advanced' tab and check 'Run in terminal'
- Click 'Save'

Now, when you open your *Reboot to macOS* app, you will be asked to enter your password, and then, your Mac will reboot onto macOS.

If you have other distros, you can also make applications such as *Reboot to Fedora*, etc. by using, for example:
```
/bin/sh -c 'sudo asahi-bless -n -y --set-boot "Fedora" && reboot'
```
"Fedora" here is the name I gave my Fedora install, which may be different you, or perhaps it may be "Gentoo", "Deepin", etc.

## Notes
This is obviously possible on other desktop environments such as xfce. Do I remember how? Nope. You can probably figure it out easily. You just need to find out where you can make your own "application".