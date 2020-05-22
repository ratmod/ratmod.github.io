# Server Manual

Ratmod servers have a variety of callvotes to change game modes or turn on/off features.

Some ratmod servers are limited to one game type. "Allmodes" and "Try Hard" servers have *all* game types built in. This makes it possible to have one server rather than a multitude.

Any game mode or option switch is done with a callvote. Use the game console with these commands:

- `\cv <option>` 
- `\cv custom <mode or option>`

!!! Info "Note"
    Please note that not all game modes / options are available on all ratmod servers. The following is meant as a reference to what is available overall. 

    If you want to see a list of available call votes on a server, use the `\cv` or `\cv custom` commands with no arguments.


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






## Available Game Modes via `\cv custom`

Mode | What it is:
---- | ----------
1fctf | [One Flag CTF](https://openarena.fandom.com/wiki/One_Flag_Capture)
ca | [Clan Arena a.k.a Elimination](https://openarena.fandom.com/wiki/Elimination)
ctf | [Capture the Flag](https://openarena.fandom.com/wiki/Manual/Gamemodes#Capture_The_Flag_.28CTF.29)
ctfe | [Capture the Flag Elimination](https://openarena.fandom.com/wiki/CTF_Elimination) (catch flag or frag enemy team for point)
duel | [Duel Mode](https://openarena.fandom.com/wiki/Manual/Gamemodes#Tournament) (1v1)
dueleq | Duel Mode with equal ping (for fairness)
extendedca | CA but with all weapons
ffa | [Free For All (Deathmatch)](https://openarena.fandom.com/wiki/Manual/Gamemodes#Free_For_All)
ffa_aw | Free For All with all weapons.
ictf | Instagib Catch the Flag
lms | [Last Man Standing](https://openarena.fandom.com/wiki/Last_Man_Standing) (FFA version of Elimination)
overload | [Overload](https://openarena.fandom.com/wiki/Manual/Gamemodes#Overload) - destroy the other teams obelisk.
tdm | [Team Death Match](https://openarena.fandom.com/wiki/Manual/Gamemodes#Team_Deathmatch)
th | Treasure Hunt
xterm | Extermination a.k.a. xterm



## Available Options via `\cv custom`

Option | What it does:
------ | -------------
autolock | ?
awardpushing | Enable/Disable getting a point for pushing a player off the map or into lava etc.
cup | ?
fastrg | ?
fastswitch | Enable/Disable fast weapon switching (?describe more?). 
freerj | Enable/Disable Free Rocket Jump (no self-damage when you rocket jump)
friendlyfire | Enable/Disable Friendly Fire (for team modes). In CTF it is off by default. In TDM it is on by default.
friendswh | ?
grapple | Enable/Disable Grapple (if on it is always available)
insta | Enable/Disable Instagib for the current game mode
inviswalls | Enable/Disable Invisible walls (turns off map clipping). In TH this is on by default.
kamikaze | Enable kamikaze (?)
midair | ?
mute | Mute the spectators.
nokamikaze | Disable kamikaze (?)
nopowerups | Disable powerups
overtime | ?
powerups | Enable powerups
railjump | Enable/Disable Rail jump (like rocket jump, with rail)
rampjump | Enable/Disable Ramp jump
ratmode | Enable/Disable rat mode. Different CPMA like physics.
ready | Enable/Disable the Ready system. By default it is off.
rockets | Enable/Disable Only rockets for current game mode
skinsbright | Force all players to see bright skins
skinsnormal | Force all players to see normal skins
skinsoutline | Force all players to see outline skins
smoothjump | ?
taunts | Enable/Disable special taunts.
telemissiles | Enable/Disable projectiles going through the teleport. On by default.
throughwalls | Enable/Disable damage through walls and floors.
unmute | Unmute the spectators.
vampire | Enable/Disable vampire mode. - description?



## The Team Queue System

There is now a queue system available for team-based modes. The intention of this system is to make sure the teams have equal numbers. It only allows people to join in pairs, which ensures that joining players cannot create unequal teams.

This is not yet on by default and it is a vote: `\cv custom queues`

- All people waiting in queue will be shown on the scoreboard. Red "queue" text means the player is waiting to join the red team. Blue text for blue team. White text is for those who auto-joined.
- All people waiting in queue will be spectating the game and will have a message on their screen "Waiting to join team (red/blue)

### Joining Games
When the queue system is turned on, this is how it handles a few common situations:

#### Situation: A player wants to be ready to play...
A good way to indicate that you want to play is just to join. Other spectators can then see on the scoreboard that you want to play and which team you want to join. As soon as someone else joins the opposite team or auto-join, you will enter the game.

#### Situation: spectators want to join the game...
- If someone from spectators tries to join a team, they will go into the queue.
- For example, Player A joins red and is in queue for red. When Player B joins blue, they will both be added to the game. 
- If Player B accidentally joins red, both players will be in the queue for the red team. Without the queue system, both players would be on team red and team red would win!

### Balancing
In addition to the queues, the vote also enables a re-balancing system that makes sure the teams have equal numbers of players even if players leave during the game:

#### Situation: A player leaves a team...
- If the teams become unequal because one or more of the players leave, then the game will equalize the player numbers. The server will wait for a few moments before taking action. 
- In XTERM/CA this balancing will happen after the current round is finished. In CTF it will happen after a few moments. The server will also display messages in the console and on the screen that this will happen.
- Who is put into the queue? The last player who joined will be put back into his team's queue. In the case that all players joined at the same time it will be the one with the lowest score.

#### Situation: Two players want to switch teams
- The queue system makes it easier to handle players switching to opposite teams. 
- Player A switches from blue to red and will be in the red queue. If someone doesn't switch very soon from red to blue, the server will equalize the number of players - moving a red player to the queue.
