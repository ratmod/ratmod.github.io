# Performance Tweaks

These are settings you may want to use in case the game has performance issues on your computer (low or unstable FPS).

## Engine Tweaks 

A basic thing you can do to improve is to reduce the resolution. 

Ioquake3 supports both opengl1 and opengl2 as a backend, but opengl2 is much slower on some machines. If your engine has the `cl_renderer` setting, try setting it to `opengl1`:

	cl_renderer opengl1

Disabling dynamic lights can also help:

	r_dynamicLight 0

If that doesn't help enough, you may want to disable some shader stages marked as "detail":

	r_detailTextures 0

You can also try reducing the geometric details (higher number = less detail):

	r_subdivisions 11
	r_subdivisions 21

Also reduces geometric details:

	r_lodbias 1

This setting may cause performance issues if it's disabled:

	r_allowExtensions 1

You can also disable the sky:

	r_fastSky 1

Lastly, you can use vertex lighting. This should probably be the last option you try since it significantly reduces quality:

	r_vertexLight 1

## Mod-specific tweaks

There are are also certain mod settings that can have en effect on performance. Especially settings that create a lot of individual rendering entities can have a negative impact on performance.
One such example is projectile trails, which you can disable with:

	cg_noprojectileTrail 1

If you are using the new ratmod statusbar (`cg_ratStatusbar 4-5`), you can disable some of the decor elements:

	cg_drawHabarDecor 0

as well as the background:

	cg_drawHabarBackground 0

(this is disabled by default already)

Some more settings that may help:

	cg_drawFPS 2
	cg_simpleItems 1
	cg_ratRailBeefy 0

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
