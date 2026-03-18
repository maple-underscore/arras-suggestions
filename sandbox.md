# Command improvements!!!

- `$rank`
  
  Has the following subcommands:
  
  - `set` - Sets a rank for a player
    
    Takes in the following arguments:
    
    - `id` - Player ID
    - `perms` - Permissions to give to the player
    - `attr` - Attributes to assign to the player
    - `name` - (optional) Gives a name to the role
   
    Example: `$rank set 12345 [build, spec] [as, ao] Builder` to create a rank which can only build and become spectator, and can be assigned by AS and AO.
      
  - `list` - Lists all available ranks
 
    Example: `$rank list`
    
  - `get` - Gets permissions and attributes of a rank
    
    Takes in the following arguments:
    
    - `name` - Name of the rank to get
   
    Example: `$rank get Builder`
   
  - `del` - Deletes a certain rank
 
    Takes in the following arguments:
   
    - `name` - Name of the rank to delete
   
    Example: `$rank del Builder`

- `$arena`

  Has the following subcommands:
 
  - `spawnpoint` - Sets spawnpoint
 
    Takes in the following arguments:
   
    - `position` - Position to spawn at
   
    Example: `$arena spawnpoint 0 0` sets spawnpoint at `(0, 0)`

  - `spawnregion` - Sets spawnpoint as a region
 
    Takes in the following arguments:
   
    - `corner1` - A tuple defining one corner of the spawn region
    - `corner2` - A tuple defining the second corner of the spawn region
   
    Example: `$arena spawnregion (10, 10) (-10, -10)` sets the spawn region to a `20`x`20` unit square around center of the arena
   
> [!NOTE]
> Corners must be in __TUPLE__ form!
>
> This means a format like `(0, 0)` with parentheses enclosing the `x` and `y` values.
    
  - `team` - Sets number of teams

    Takes in the following arguments:

    - `teamAmount` - A number between `1`-`20` that defines the number of teams in the arena. Set to `0` for FFA

    Example: `$arena team 10` creates `10` teams
    
  - `size` - Sets arena size
 
    Takes in the following arguments:

    - `xSize` - A number between `2`-`1024` that defines the width of the arena
    - `ySize` - A number between `2`-`1024` that defines the height of the arena
   
    Example: `$arena size 100 100` creates an arena with dimensions `100`x`100`
















