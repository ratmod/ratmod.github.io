# FAQ

## What Engines are compatible with Ratmod?

Since ioquake3 is open source there are several options. These are known to work well:

- [ioquake3](https://github.com/ioquake/ioq3). If you are compiling ioquake3 on your own, make sure to do so with Ogg Vorbis support. See [below](#how-do-i-launch-ioquake3-engine) for details about how to launch the engine.
- [openarena-ioq3](https://github.com/OpenArena-Ioq3/openarena-ioq3). This is a fork of ioquake3 that is pre-configured for OpenArena and keeps up to date with the ioq3 master.
- [openarena engine](http://openarena.ws/download.php) (ioquake3+oa) (this is outdated). This is also available in various Linux distributions.
- [fx3](https://codeberg.org/ChannelZ/fX3). Based on ioq3, with various improvements (graphics & sound options, tabbed console, etc)

It is not recommended to use **yuengine**. This engine is known to produce audio and visual bugs with ratmod.

## How do I launch ioquake3 Engine?

The examples below also have the necessary arguments for increasing memory for the game.

### For Linux

Using ioquake3 engine will require you to set up a folder with the baseoa pk3s and launch the engine with the following (for linux): 

	ioquake3 +set fs_basepath "path/to/openarena/installation" \
		 +set com_homepath .openarena +set com_basegame baseoa \
		 +set com_legacyprotocol 71 +set com_protocol 72 \
		 +set sv_master1 dpmaster.deathmask.net \
		 +set com_standalone 1 +set cl_motd 0 \
         +set com_hunkMegs 256 +set com_zoneMegs 64 \
         +set com_soundMegs 32 \
		 +set cl_renderer opengl1

If you wish to start ratmod directly, you can add `+set fs_game rat` at the end of the command.

!!! Info "About `fs_basepath`"
    `fs_basepath` should point to the OpenArena installation directory, which should contain a subdirectory called `baseoa` containing `pak0.pk3` (as well as others).

!!! Info "About `com_homepath`"
    `com_homepath` will be the path that contains the configs/downloaded maps/mods. It is relative to the user's home directory.

!!! Info "About `com_protocol` and `com_legacyprotocol`"
    In OpenArena, protocol 71 refers to the legacy quake3 protocol, which confusingly is referred to as protocol 68 by quake3.
    ioquake3 supports a newer protocol, which has UDP spoofing protection and VoIP support. In order to make ioq3 compatible 
    with games that use different numbers for these protocols, the `com_protocol` and `com_legacyprotocol` cvars were added.
    Setting `com_protocol 72` and `com_legacyprotocol 71` allows your client to use the newer protocol if the server supports it.
    See also the [explanation of network protocols on the ioquake3 website](https://ioquake3.org/help/sys-admin-guide/#networkprotocols).
  

!!! Info "Regarding OpenGL2"
    **ioquake3** has an opengl2 based renderer (on by default) that might cause performance issues. You can switch to `opengl1` by setting `\cl_renderer opengl1`. 


### For Windows

The options are generally the same as for Linux, but `com_homepath` should be set to OpenArena instead.

Launch with the following:

	ioquake3 +set fs_basepath "path\to\openarena\installation" +set com_homepath OpenArena +set com_basegame baseoa +set com_legacyprotocol 71 +set com_protocol 72 +set sv_master1 dpmaster.deathmask.net +set com_standalone 1 +set cl_motd 0 +set com_hunkMegs 256 +set com_zoneMegs 64 +set com_soundMegs 32 +set cl_renderer opengl1


## Why don't brightskins/shells/outlines show up even though I configured them?

Forcing models and colors only works when the server configuration allows it.
Check `\rules` to see what the server allows.

## Can I copy my config from <insert other mod/game\> here?

While certain settings might be compatible between different mods (or even other games), there are no guarantees that it will work properly. It's more likely that something will get messed up. We recommend using a manual configuration (autoexec.cfg) containing all your settings that are common across different mods (such as the basic keybinds), but *don't* try to copy q3config.cfg between different mods.

### How do I change the status bar style?

Use `cg_ratstatusbar` with a value of:

- `0` = old-school OA statusbar
- `1` = flag on the left
- `2` = flag on right
- `3` = minimalistic version
- `4` = futuristic statusbar with health/armor bars in the center, ammo bar on the left. Also enables new powerup display
- `5` = similar to 4, but vertically flipped

## How do I turn off taunts?

You can disable taunts with `\cg_taunts 0`. Note that this will only work if the server doesn't force taunts to be on. You can check using `\rules`.
You may also be able to vote to toggle taunts off or on for everyone with `\cv custom taunts`.

## Why isn't `r_picmip` working?

This is a client-side setting, but please remember that it can be disabled by the server configuration. For example, it is disabled in the treasure hunter game type.

## Does Ratmod run on the quake3e engine?

While it *may* be possible to run OA+Ratmod on quake3e, you won't be able to join any of the servers that are running on ioq3 / ioq3+oa.

## Why do I get a "Connection Interrupted" message despite having a stable connection?

Most likely the issue is that you are playing with high FPS (say, >= 250 FPS) and your ping is also high. Due to an engine limitation, higher FPS requires lower pings. Try reducing `\com_maxfps` to a lower value.

## How do I enable VoIP?

First, you need to setup OA with ioquake3 (see above). Make sure you pass `+set com_protocol 72` to the ioquake3 command. The openarena-ioq3 fork already does this for you.

VoIP can then be enabled using `set cl_voip 1`
Then bind a key to record: `\bind somekey +voiprecord`. You should see a sound meter on the HUD while the game is recording.

Visit the [ioquake3 voip readme](https://github.com/ioquake/ioq3/blob/main/voip-readme.txt) for more details.

