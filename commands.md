# Command improvements!!!

- `$rank` - Assigns and edits ranks __[AS and AO only]__
  
  Has the following subcommands:

  - `setAttr` - Sets a specific property of a player
 
    Takes in the following arguments:

    - `id` - Player ID
    - `data` - The attributes to modify for the player (e.g. `attr=[Attributes]`)
   
    Example: `$rank setAttr 12345 perm=[build]` sets the player
    with ID `12345` to be able to build with no other perms.
    To add or remove a property use `+` or `-` in front of the list
  
  - `set` - Sets a rank for a player
    
    Takes in the following arguments:
    
    - `id` - Player ID
    - `perms` - Permissions to give to the player
    - `attr` - Attributes to assign to the player
    - `name` - (optional) Gives a name to the role
   
    Example: `$rank set 12345 [build, spec] [as, ao] Builder`
    to create a rank which can only build and become spectator,
    can be assigned by AS and AO and assigns that rank to the player with ID `12345`
      
  - `list` - Lists all available ranks
 
    Example: `$rank list`
    
  - `get` - Gets permissions and attributes of a rank
    
    Takes in the following argument:
    
    - `name` - Name of the rank to get
   
    Example: `$rank get Builder`
   
  - `del` - Deletes a certain rank
 
    Takes in the following argument:
   
    - `name` - Name of the rank to delete
   
    Example: `$rank del Builder`

- `$arena` - Modifies properties of the arena __[AO only]__

  Has the following subcommands:

  - `broadcast` - Broadcasts a global message
 
    Takes in the following argument:

    - `message` - A string containing the message content
   
    Example: `$arena broadcast "Test message here"`
 
  - `spawnpoint` - Sets spawnpoint
 
    Takes in the following argument:
   
    - `position` - Position to spawn at
   
    Example: `$arena spawnpoint 0 0` sets spawnpoint at `(0, 0)`

  - `spawnregion` - Sets spawnpoint as a region
 
    Takes in the following arguments:
   
    - `corner1` - A tuple defining one corner of the spawn region
    - `corner2` - A tuple defining the second corner of the spawn region
   
    Example: `$arena spawnregion (10, 10) (-10, -10)` sets the spawn region
    to a `20`x`20` unit square around center of the arena
    
  - `team` - Sets number of teams

    Takes in the following argument:

    - `teamAmount` - A number between `1`-`20` that defines the number of teams in the arena. Set to `0` for FFA

    Example: `$arena team 10` creates `10` teams
    
  - `size` - Sets arena size
 
    Takes in the following arguments:

    - `xSize` - A number between `2`-`8192` that defines the width of the arena
    - `ySize` - A number between `2`-`8192` that defines the height of the arena
   
    Example: `$arena size 100 100` creates an arena with dimensions `100`x`100`

  - `polygon` - Sets the polygon limit

    Takes in the following argument:

    - `limit` - An integer that represents the maximum number of polygons allowed at any time
   
    Example: `$arena polygon 1000` sets polygon cap to `1000`

- `$get` - Gets a specific data attribute of the specified player(s) __[Available to all players]__

  Has the following subcommands:

  - `id` - Used to get the iD of the specified player(s)

   Example: `$get id "Testing"` gets the Player ID of the player `"Testing"`
  
  - `rank` - Used to get the rank of the specified player(s)
 
    Both of these take the following argument:

    - `namespace` - Either a player name as a string (e.g. `"Testing"`),
    - a list (e.g. `["Testing", "d2"]`) or `all` to get all players.
   
    Example: `$get rank "Testing"` gets the rank of the player `"Testing"`
   
- `$map` - Used to modify the map __[Mixed rank]__

  Has the following subcommands:
  
  - `export` - Used to export the map as a string __[AC, AS and AO only]__
 
    Example: `$map export` copies the map string to the clipboard

  - `import` - Used to import a map from a string __[AO only]__
 
    Takes in the following argument:

    - `mapData` - A string containing the data for the map to import.
   
    Example: `map import {mapData}` imports the map.

- `$boss` - Used to set boss properties __[AO only]__

  Has the following subcommands:

  - `interval` - Used to set boss spawn interval
 
    Takes the following arguments:

    - `minimumTime` - Minimum time between boss spawns
    - `maximumTime` - Maximum time between boss spawns

    Using only one argument sets the boss time to exactly that argument. Otherwise, the boss time is randomized between the set values to the nearest millisecond.

    Optional time extensions (default is in seconds): [t, ms, s, m, h] where t is ticks.

    Delay is capped at `1` millisecond minimum and `24` hours or `1` day maximum
    [`1440` minutes, `86400` seconds, `2592000` ticks, `86400000` milliseconds]
   
    Example: `$boss interval 10m 15m` sets a boss to spawn between every `10` and `15` minutes

  - `level` - Used to set boss difficulty
 
    Takes the following argument:

    - `types` - A list of possible boss types from
      [elite, nester, terrestrial, celestial, eternal]

    Example: `$boss level [elite, nester]` only allows Elites and Nesters to spawn

  - `spawning` - Used to set boss spawning toggle
 
    Takes the following argument:

    - `toggle` - A boolean to enable or disable boss spawning (`True` or `False`)
   
    Example: `$boss spawning False` disables boss spawning

## Details

> [!NOTE]
> Ranks are indicated with their specific integer in player list.
> Hovering over the integer will display the rank name, permissions and attributes.
>
> Multiple Player IDs may be specified using a list (e.g. `[12345, 67890]`)
>
> If you have quotes or special characters in any arguments,
> use a reverse solidus or backslash (`\`) to escape the special character(s).
>
> You may use the `$` character to treat a nested command's output as an argument in the parent command.
> e.g. `$get rank $get all$` will return the rank of all players.
