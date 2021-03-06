# binja-ui-tweaks
UI Tweaks for Binary Ninja.

As of now, the tweaks seem to be rather stable on Ubuntu 16.06 and Windows 8.1, other platforms are unknown.

# Usage / Installation

Place the `tweak-installer.py`, `.tweaks`, and `UITweaks` in the plugin directories. 

Available tweaks are listed in .tweaks. If you want to disable certain tweaks, you can comment them out by prefixing them with a `#`. 

By default all tweaks are enabled.

## UI Wtih All Current Tweaks Applied 

![Image of All Available Tweaks](http://i.imgur.com/eyiojnd.png)

## Known Bugs

The BinaryNinja API does not expose the current view, or current function through the PythonAPI. You have to get them from a Plugin callback. These Tweaks operate independantly of the plugin system, but they need access to the current view and function. In order to solve this problem, we register a function plugin callback that is invoked (via a leaked QAction) when we need the current function or view. This is super hacky, and results in a lot of spam in the Log window (because everytime a plugin completes, it prints out the time it took to execute).

Tweak specific bugs can be viewed by selecting the relevent label on the `Issues` page of this project

# Suggestions

If you have suggestions for UI modifications, open a pull request and we can talk about it :)

# Dependencies 

1. Ubuntu 16.04, Win8.1 (only platforms tested)
2. Binary Ninja [Version 1.0.dev-579]
3. PyQt5 [Python 2.7] (Ubuntu Repo Version) (Built from source on Win8.1)
4. [binja-ui-api](http://www.github.com/nbsdx/binja-ui-api)

Instructions for building PyQt5 for Python2.7 on Windows will be released shortly. In the meantime, I figured it out from these two links: 

*http://blog.abstractfactory.io/pyqt5-1-1-for-python-2-7/
*https://gist.github.com/nbsdx/67f41bdc12cc6728d0727a73c5b1ca3f

OSX testing will be coming in a bit, I want to get Win8.1 and Ubuntu settled first.

# Features

## Sortable Function Window

This tweak allows you to sort the function list via a header at the top of the panel. Clicking on the panel will change the sort direction (signified by an arrow pointing up or down).

## Function Graph Preview

Gives you a high-level overview of your function - similar to IDA's. It's located in the `Graph` tab next to `Xrefs`. Click on the graph to move the current view.

