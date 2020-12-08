# Waveform (Minecraft Mod)
Waveform is a mod idea that I have that customizes the music that plays in Minecraft: Java Edition. Basically, Dynamic Sounds. It uses position, biome, dimension, time, health, weather, y level, and more.

## Variables

|Key|Description|Value|
|-|-|-|
|Title Screen|Whether to play on the title screen or not|None|
|Time|How old the world is|Integer|
|Sun Position|Sunrise, Midday, Sunset, Midnight, Day, Night|Choice|
|Weather|Clear, Rain, Thunderstorm, Snow, Snowstorm|Choice|
|Y Pos|How high or low in the world the person is|Integer|
|Biome|What biome the person is in|String|
|Dimension|Overworld, Nether, End, etc. Default is Overworld if not mentioned.|String|
|In Battle|Whether hostile mob is trying to attack the player|None|
|In Battle w (Enemy)|Fighting a specific hostile mob, depends on mob closest to you|Choice|
|Structure|In or around (20 blocks) a structure. Nether Fortress, Village, etc.|String|
|Death|To play on death|None|
|Interacting w Dog|Feeding Dog, Dog Following|None|
|Fight w Dog|In Battle with dog helping|None|
|Interacting w Cat|Feeding Cat, Cat Following, Cat Scaring Creeper|None|
|Default|Plays when any of the others can't|None|
|Distance from Spawn|How far away from spawn a player is|Integer|
|Near Player|If player is near (50 blocks) another player|None|
|Wet|In water for more than 20 seconds or in sea biome, below sea level or having nautilus effect|Boolean|
|Music Disc|Can be enabled or disabled in settings.|None|

### Setup
1. Song (Key=Value, Repeat)

## Commands
#### `/waveform`, `/wf`
Gives a list of commands and what they do.

#### `/song <song> [synced] [entity]`
Plays `<song>` everywhere if `[synced]` (default) is true. If false, then only plays for certain entity specified as `[entity]`.

#### `/waveform list [song]`, `/wf list [song]`
Sends a list of all the songs that are dynamic if `[song]` isn't specified. List values can be clicked to send the command `/wf list [song]` to chat, to give info. If specified, then it gives information on that song. Information includes keys, values, percentages, and whether the person is currently applicable for this song to be played.

#### `/waveform get [player]`, `/wf get [player]`
If `[player]` isn't specified, says what song is currently playing and what that song's keys and values and percentages are for the person sending the command. If `[player]` is specified, than it shows info on that person. If `@a` is entered, then shows info for each person.

#### `/waveform set <setting> <value>`
Changes the current value of a setting to `<value>`.

## Songs
### Minecraft - Volume Alpha (C418)
1. Key ()
2. Door
3. Subwoofer Lullaby
4. Death
5. Living Mice
6. Moog City
7. Haggstrom
8. Minecraft (Title SunPosition=Sunrise)
9. Oxygene
10. Equinoxe
11. Mice on Venus
12. Dry Hands
13. Wet Hands
14. Clark
15. Chris
16. Thirteen
17. Excuse
18. Sweden
19. Cat
20. Dog
21. Danny
22. Beginning
23. Droopy Likes Ricochet
24. Droopy Likes Your Face

### Minecraft - Volume Beta - Main (C418)
1. Ki
2. Alpha
3. Dead Voxel
4. Blind Spots
5. Flake
6. Moog City 2
7. Concrete Halls
8. Biome Fest Mutation
9. Haunt Muskie
10. Warmth
11. Floating Trees (Time=Day and Weather=Clear)
12. Aria Math
13. Kyoto
14. Ballad of the Cats
15. Taswell
16. Beginning
17. Dreiton
18. The End
19. Intro

### Minecraft - Volume Beta - Discs (C418)
1. Chirp (Music Disc)
2. Wait (Music Disc)
3. Mellohi (Music Disc)
4. Stal (Music Disc)
5. Strad (Music Disc)
6. Eleven (Music Disc)
7. Ward (Music Disc)
8. Mall (Music Disc)
9. Blocks (Music Disc)
10. Far (Music Disc)

### Minecraft - Aquatic Update (C418)
1. Axolotl
2. Shuniji
3. Dragon Fish

### Minecraft - Nether Update (Lena Raine)
1. Chrysopoeia
2. Rubedo
3. So Below
4. Pigstep - Mono Mix
5. Pigstep - Stereo Mix

## Settings

|Setting|Description|Type|Default|
|-|-|-|-|
|Enabled|Enables the whole entire mod|Boolean|True|
|Custom Sounds|Whether to get custom sounds from resource pack or not|Boolean|True|
|Client Side|Disables non client side features, like structure and battle music.|Boolean|False|
|Prime Color|Primary color when using chat. Numbers to color escape codes.|Integer|36|
|Second Color|Secondary color when using chat. Numbers to escape codes.|Integer|32|
|Visualizer|Shows waveform of current song in top right hand corner of the screen.|Boolean|False|
|Music Disc Ambience|Whether music disc songs can be added to the rotation of songs.|Boolean|False|

## License
Just as a note, all rights reserved. If you wish to create this mod, you can contact me. Thank you.