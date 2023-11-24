# Fuzzy find and open the most recently used files in vis

Use [fzf](https://github.com/junegunn/fzf) to open the most recently used files in [vis](https://github.com/martanne/vis).

## Usage

In vis:
- `:fzfmru`

## Configuration

In visrc.lua:

```lua
plugin_vis_mru = require('plugins/fzf-mru')

-- Path to the fzf executable (default: "fzf")
plugin_vis_mru.fzfmru_path = "fzf"

-- Arguments passed to fzf (default: "")
plugin_vis_mru.fzfmru_args = "--delimiter / --nth -1" -- Search only by file names

-- File path to file history (default: "$HOME/.mru") 
plugin_vis_mru.fzfmru_filepath = "/Users/Username/.vismru"

-- The number of most recently used files kept in history (default: 20)
plugin_vis_mru.fzfmru_history = 10

-- Mapping configuration example (<Space>b)
vis.events.subscribe(vis.events.INIT, function()
    vis:map(vis.modes.NORMAL, " b", ":fzfmru<Enter>")
end)
```

## Tips

Fuzzy find the most recently used files from the current directory hierarchy:

```lua
plugin_vis_mru = require('plugins/fzf-mru')
plugin_vis_mru.fzfmru_path = 'grep "^'..os.getenv('PWD')..'" | fzf'
```

## Inspired by

- [vis-fzf-open](https://github.com/guillaumecherel/vis-fzf-open/)
- [vis-cursors](https://github.com/erf/vis-cursors)
