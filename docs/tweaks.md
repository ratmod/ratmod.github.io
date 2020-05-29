# Performance Tweaks

These are settings you may want to use in case the game has performance issues on your computer (low or unstable FPS). Try changing one setting at a time and check if it is stable.

*Note: changing some of these settings may require you to restart the video renderer. Use the command `\vid_restart` to do so.*

First, make sure to set your FPS: `com_maxfps 125`. If you don't see the FPS on your HUD, set `cg_drawFPS 1`.

## Engine Tweaks 

The first thing you should try to do to improve performance is to **reduce the resolution**. The easy way to do this is through the UI menu.  

Ioquake3 supports both opengl1 and opengl2 as a backend, however opengl2 is much slower on some machines. If your engine has the `cl_renderer` setting, try setting it to `opengl1`:

	cl_renderer opengl1

Disabling dynamic lights can also help:

	r_dynamicLight 0

If that isn't enough, you may want to disable some shader stages marked as "detail":

	r_detailTextures 0

You can disable hardware multi-texturing: 

	r_ext_multitexture 0

You can also try reducing the geometric details (a higher number = less detail):

	r_subdivisions 11
	r_subdivisions 21

Or reduce geometric details:

	r_lodbias 1  // can set up to 4

Disabled extensions *might* cause performance issues. Enable them:

	r_allowExtensions 1

You can also disable the sky, but be aware that on some maps this also makes it so you can't see through portals:

	r_fastSky 1

Lastly, you can use vertex lighting. This should probably be the last option you try since it significantly reduces quality (use `r_dynamiclight 0` and `r_detailtextures 0` in order to benefit from this:

	r_vertexLight 1	

## Mod-specific tweaks

There are are also certain mod settings that can have an affect on performance. This is especially true with settings that create a lot of individual rendering entities.

One such example is projectile trails, which you can disable with:

	cg_noprojectileTrail 1

If you are using the new ratmod statusbar (`cg_ratStatusbar 4-5`), you can disable some of the decor elements:

	cg_drawHabarDecor 0

as well as the background (which is disabled by default already):

	cg_drawHabarBackground 0

Some more settings that may help:

	cg_drawFPS 2 
	cg_simpleItems 1     // use 2D icons for map items
	cg_ratRailBeefy 0    // more simple rail trail

Disabling the rail spiral can help as well:

	cg_ratRailRadius 0

You can also try a different statusbar:

	cg_ratStatusBar 3

Or even more minimalistic:

	cg_ratStatusBar 1
	cg_ratStatusBar 2

If you are playing with brightshells and noticing that performance drops when there are many players on, you may want to use the old, simpler bright skins instead of the brightshell overlays:

	set cg_enemyModel smarine/bright
	set cg_teamModel sarge/bright
