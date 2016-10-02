# binja-ui-tweaks
UI Tweaks for Binary Ninja. Seems kinda stable, I just got it working, so there may be some things that I missed. 

Stability could be totally killed by any future updates to Binary Ninja, so take caution applying tweaks after an update.

## UI Wtih All Current Tweaks Applied 

![Image of Yaktocat](http://i.imgur.com/pkSQry4.png)

## Known Bugs

The BinaryNinja API does not expose the current view, or current function through the PythonAPI. You have to get them from a Plugin callback. These Tweaks operate independantly of the plugin system, but they need access to the current view and function. In order to solve this problem, we register a function plugin callback that is invoked (via a leaked QAction) when we need the current function or view. This is super hacky, and results in a lot of spam in the Log window (because everytime a plugin completes, it prints out the time it took to execute). 

# Suggestions

If you have suggestions for UI modifications, open a pull request and we can talk about it :)

# Dependencies 

1. Ubuntu 16.04 (only platform tested)
2. Binary Ninja (only dev channel has been tested)
3. PyQt5 (Ubuntu Repo Version)
4. [binja-ui-api](http://www.github.com/nbsdx/binja-ui-api)

# Usage

Place the `tweak-installer.py`, `.tweaks`, and `UITweaks` in the plugin directories. 

Available tweaks are listed in .tweaks. If you want to disable certain tweaks, you can comment them out by prefixing them with a `#`. 

By default all tweaks are enabled.

# Features

## Sortable Function Window

This tweak allows you to sort the function list via a header at the top of the panel. Clicking on the panel will change the sort direction (signified by an arrow pointing up or down).

### Bugs

* No known bugs

## Function Graph Preview

Gives you a high-level overview of your function - similar to IDA's. It's located in the `Graph` tab next to `Xrefs`

### Bugs

1. Rendering the image takes a lot of resources, so if you're resizing it with a large function, there will be some lag. 
   * Might look at rendering an SVG image that can be resized more easily when you enter a new function
