# Spotify

**WARNING**: Check [this](./widevine.md) out first!\
**Recommended Software**: [Chromium](https://search.nixos.org/packages?channel=25.05&show=chromium&query=chromium)

It is no secret Spotify isn't officially supported for `aarch64-linux`.\
However, it's still absolutely possible to get Spotify up in a few ways, the most popular one being simply using the web player (which is what we'll be doing here, using a trick to make it more appealing).

The recommended browser for this guide is `Chromium`, as it has the `--app` feature: it is as simple as:
```bash
chromium --app="https://open.spotify.com"
```

This will open a new, dedicated Chromium tab with the Spotify Web Player. However, there's a way to make it better:  by making this into an app.

On KDE Plasma:
- Right click Kickoff (Application Launcher) > Edit Applications
- Click on a category of your choice (I recommend Multimedia, it doesn't matter anyway)
- Click 'New Item', name it 'Spotify'
- On the 'Program:' field, enter:
```bash
chromium --app="https://open.spotify.com"
```
- Click 'Save'

You're good to go! Of course, you can always use things such as [```spotify-player```](https://github.com/aome510/spotify-player) instead if you want to...