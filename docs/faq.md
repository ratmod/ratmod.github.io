# FAQ

### What Engines are compatible with Ratmod?

Since ioquake3 is open source there are several options. These are known to work well:
- [ioquake3](https://github.com/ioquake/ioq3). If you are compiling ioquake3 on your own, make sure to do so with Ogg Vorbis support. Using ioquake3 engine will require you to set up a folder with the baseoa pk3s and launch the engine with the following (for linux): `path/to/ioq3 +set com_basegame "baseoa" +set com_legacyprotocol 71 +set com_protocol 71 +set sv_master1 dpmaster.deathmask.net +set fs_basepath "path/to/parent/folder/of/baseoa/pk3/folder" +set fs_homepath "/path/to/username/.openarena"`
- [openarena engine](http://openarena.ws/download.php) (ioquake3+oa) (this is outdated). This is also available in various Linux distributions.
- [fx3](http://www.h4l-group.de/pub/Q3_engines/fX3/client/for_OA/)

It is not recommended to use **yuengine**. This engine is known to produce audio and visual bugs with ratmod.

### Why don't brightskins/shells/outlines show up even though I configured them?

Forcing colors only works when the server configuration allows it.

### Can I copy my config from \<insert other mod/game\> here?

While certain settings might be compatible between different mods (or even other games), there is no guarantee of that and you will almost certainly end up messing something up. We recommend using a manual configuration (autoexec.cfg) containing all your settings that are common across different mods (such as the basic keybinds), but *don't* try to copy q3config.cfg between different mods.

### How do I change the status bar style?

Use `cg_ratstatusbar` with a value of:

- `0` = old-school OA statusbar
- `1` = flag on the left
- `2` = flag on right
- `3` = minimalistic version
- `4` = futuristic statusbar with health/armor bars in the center, ammo bar on the left. Also enables new powerup display
- `5` = similar to 4, but vertically flipped