# You should know...

## Swap
- If you are using Asahi Linux on a Silicon Mac with 8 GB (7.4 GiB) RAM (namely a MacBook), no matter the distribution, you **MUST** set up swap. Trust me, if you don't, things won't be so pretty. Here's the output of my ```free``` command, running Chromium with about 20 tabs open, as well as VSCodium and Kate, for reference:
```bash
               total        used        free      shared  buff/cache   available
Mem:           7.4Gi       5.7Gi       434Mi       1.3Gi       2.7Gi       1.7Gi
Swap:           11Gi       868Mi        11Gi
```

Although it doesn't look *thaaaat* bad, it depends on how your Mac is feeling that day. In any case, if I had no swap, if that "free" RAM went under probably around 200Mi, things would start going very wrong. It's always good to make sure :)

Anyway, you should set up swap even if your Mac has a good amount of RAM. If you're asking why, well, I'm asking: why not?