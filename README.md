![A*](https://github.com/selimanac/defold-astar/blob/master/assets/defoldheader.png?raw=true)

This is a path finder and A* solver (astar or a-star) native extension for [Defold Engine](https://www.defold.com/) build on [MicroPather](https://github.com/leethomason/MicroPather). 

**Caution:** This extension is not battle tested yet and you should consider it as alpha release. It may contain bugs.

## Installation

You can use the A* extension in your own project by adding this project as a [Defold library dependency](http://www.defold.com/manuals/libraries/).  
Open your game.project file and in the dependencies field under project add:

>https://github.com/selimanac/defold-astar/archive/master.zip


## API

#### astar.setup(map_width, map_height, direction, allocate, typical_adjacent, cache)

>
##### map_width
Width of your map. This is generally width of your tilemap.  
>
##### map_height
Height of your map. This is generally width of your tilemap.
>   
#####direction
Movement direction. You have two options:  
**astar.DIRECTION_FOUR**: On a square grid that allows 4 directions of movement using Manhattan distance  
**astar.DIRECTION_EIGHT**: On a square grid that allows 8 directions of movement using Euclidean distance
>
##### allocate
How many states should be internally allocated at a time. This can be hard to get correct. The higher the value, the more memory Patfinder will use.
>
- If you have a small map (a few thousand states?) it may make sense to pass in the maximum value. This will cache everything, and MicroPather will only need one main memory allocation. For a chess board, allocate  would be set to 8x8 (64)
- If your map is large, something like 1/4 the number of possible states is good.
- If your state space is huge, use a multiple (5-10x) of the normal path. "Occasionally" call `astar.reset_cache()` to free unused memory.
>
##### typical_adjacent
Used to determine cache size. The typical number of adjacent states to a given state. (On a chessboard, 8.) Higher values use a little more memory.
>
##### cache
Turn on path caching. Uses more memory (yet again) but at a huge speed advantage if you may call the pather with the same path or sub-path, which is common for pathing over maps in games.




```lua
player.build_path("<FULL_PATH>/res/common/assets/") -- Set build path when working on Editor only s
```