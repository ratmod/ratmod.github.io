# Callvote Reference

Ratmod servers have a variety of callvotes to change game modes or turn on/off features.

Some ratmod servers are limited to one game type. "Allmodes" and "Try Hard" servers have *all* game types built in. This makes it possible to have one server rather than a multitude.

Any game mode or option toggle is done with a callvote. Use the game console with these commands:

- `\cv <option>` 
- `\cv custom <mode or option>`

!!! Info "Note"
    Please note that not all game modes / options are available on all ratmod servers. 

    If you want to see a list of available call votes on a server, use the `\cv` or `\cv custom` commands with no arguments.

Since custom votes are configured differently on any given server, please check in the server for custom votes with `\cv custom`. 


## Available Votes via `\cv`

Vote | What it does
---- | ------------
map_restart | Restart the current map.
nextmap | Load the next map in the rotation.
map <mapname\> | Change the map by name.
clientkick <clientnumber\> | Kick another player (this is by the client number)
g_doWarmup | Toggle the pre-match warmup. ?
timelimit <time\> | Change the match time limit. `0` is unlimited.
fraglimit <frags\> | Change the frag limit. `0` is unlimited.
bots <n\> | Set the number of bots. `0` to kick all bots. For team modes this is bots per team.
botskill <n\> | Set the skill level of the bots. `1` is easiest and `5` is the hardest.
lock | Lock the teams.
unlock | Unlock the teams.
arena <n\> | Vote for an arena. Try between 0-8.
votenextmap | Change to the next map with the voting interface.

