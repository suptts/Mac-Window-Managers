# Mac-Window-Managers
How to use tilling Window Manager (No windows are hidden mode, no wasted screen, multi-monitor support)

```bash
brew install --cask iterm2
brew install neovim
brew install ripgrep
brew install node
```

# Install Yabai and Skhd
```bash
brew install koekeishiya/formulae/yabai
brew install koekeishiya/formulae/skhd

cd ~
mkdir .config/yabai
cd .config/yabai

touch yabairc
```

## Add Configuration Options to File

```bash
# default layout (can be bsp, stack or float)
yabai -m config layout bsp

# new window spawns to the right if vertical split, or bottom if horizontal split
yabai -m config window_placement second_child

# padding set to 10px
yabai -m config top_padding 10
yabai -m config bottom_padding 10
yabai -m config left_padding 10
yabai -m config right_padding 10
yabai -m config window_gap 10

# -- mouse settings --

# center mouse on window with focus
yabai -m config mouse_follows_focus on

# modifier for clicking and dragging with mouse
yabai -m config mouse_modifier alt
# set modifier + left-click drag to move window
yabai -m config mouse_action1 move
# set modifier + right-click drag to resize window
yabai -m config mouse_action2 resize

# when window is dropped in center of another window, swap them (on edges it will split it)
yabai -m mouse_drop_action swap


# disable specific apps
yabai -m rule --add app="^System Settings$" manage=off
yabai -m rule --add app="^Calculator$" manage=off
yabai -m rule --add app="^Karabiner-Elements$" manage=off
yabai -m rule --add app="^QuickTime Player$" manage=off
```


# Start Yabai

`brew services start yabai`

# Restart yabai:

`brew services restart yabai`

# Start Skhd

`brew services start skhd`

# Restart skhd:
`brew services restart skhd`

# Create Skhd Config File in Home Directory
```bash
cd ~
mkdir .config/skhdrc
cd .config/skhdrc

touch skhdrc
```

## Add Configuration Options to skhdrc 
```bash
# -- Changing Window Focus --

# change window focus within space
alt - j : yabai -m window --focus south
alt - k : yabai -m window --focus north
alt - h : yabai -m window --focus west
alt - l : yabai -m window --focus east

#change focus between external displays (left and right)
alt - s: yabai -m display --focus west
alt - g: yabai -m display --focus east

# -- Modifying the Layout --

# rotate layout clockwise
shift + alt - r : yabai -m space --rotate 270

# flip along y-axis
shift + alt - y : yabai -m space --mirror y-axis

# flip along x-axis
shift + alt - x : yabai -m space --mirror x-axis

# toggle window float
shift + alt - t : yabai -m window --toggle float --grid 4:4:1:1:2:2


# -- Modifying Window Size --

# maximize a window
shift + alt - m : yabai -m window --toggle zoom-fullscreen

# balance out tree of windows (resize to occupy same area)
shift + alt - e : yabai -m space --balance

# -- Moving Windows Around --

# swap windows
shift + alt - j : yabai -m window --swap south
shift + alt - k : yabai -m window --swap north
shift + alt - h : yabai -m window --swap west
shift + alt - l : yabai -m window --swap east

# move window and split
ctrl + alt - j : yabai -m window --warp south
ctrl + alt - k : yabai -m window --warp north
ctrl + alt - h : yabai -m window --warp west
ctrl + alt - l : yabai -m window --warp east

# move window to display left and right
shift + alt - s : yabai -m window --display west; yabai -m display --focus west;
shift + alt - g : yabai -m window --display east; yabai -m display --focus east;


# move window to prev and next space
shift + alt - p : yabai -m window --space prev;
shift + alt - n : yabai -m window --space next;

# move window to space #
shift + alt - 1 : yabai -m window --space 1;
shift + alt - 2 : yabai -m window --space 2;
shift + alt - 3 : yabai -m window --space 3;
shift + alt - 4 : yabai -m window --space 4;
shift + alt - 5 : yabai -m window --space 5;
shift + alt - 6 : yabai -m window --space 6;
shift + alt - 7 : yabai -m window --space 7;

# -- Starting/Stopping/Restarting Yabai --

# stop/start/restart yabai
ctrl + alt - q : brew services stop yabai
ctrl + alt - s : brew services start yabai
ctrl + alt - r : brew services restart yabai
````

# Stop/Start/Restart Yabai
```bash
# stop/start/restart yabai
ctrl + alt - q : brew services stop yabai
ctrl + alt - s : brew services start yabai
ctrl + alt - r : brew services restart yabai
```


