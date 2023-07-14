# Mac OS Shortcut
การเรียกใช้ shortcut keyboard เพื่อให้เราใช้งานโปรแกรมต่างๆได้รวดเร็ว โดย default เราสามารถเรียกใช้งาน Mac OS shortcut หรือสร้าง new shortcuts ตัวย่างเช่น

1. เปิดโปรแกรม **Mission Control** โดยการกดปุ่ม  **Control + Up Arrow** พร้อมกัน เราจะเห็นจำนวน Windows Desktops ที่เรามีอยู่ ถ้าอยากมีเพิ่มให้กดที่เครื่องหมายบวก (+) (ลองเพิ่มสัก 7 อัน)
2. ถ้าจะปิด Mission Control ก็กด **Control + Down Arrow** หรือ ใช้ สามนิ้วลากลงที่trackpad (tree singer swipe down on a trackpad) หรือจะกด Control + Up Arrow ซำ้เพื่อปิดก็ได้ 
3. ในการควบคุมหรือเข้าไปในแต่ desktops (บางทีอาจเรียกว่า spaces window) เราสามารถสั่ง switch between จอทั้งหมดได้ด้วยการกดปุ่ม **Control + rigth and left Arrows** พร้อมๆกัน (แต่ก็ยังไม่ดีพอ)
5. ดังนั้นแนะนำให้ไป create shortcut keyboard เองเช่น โดยไปเซตที่ System Setting->Keyboard->Keyboard Shortcuts-> Mission control--> Mission control and expand เพื่อเลือก **Switch to Desktop 1- Switch to Desktop 7**, แล้วกดปุ่ม **Done** เมื่อเลือกครบ
6. ให้เราไปเซต "Reduce motion" เพื่อให้การ switch ไปมามัน smoothมากขึ้นและรวดเร็วเมื่อเรากดไปมาเช่น n ^1  แล้วเลือก ^2 เป็นต้น ให้เราไปเซตทีี่  System Setting->Accessiblity-->Display แล้วให้เปลี่ยนเป็น enable "Reduce Motion"  
7. สุดท้ายให้ไปปิด **Automatically rearrange Spaces based on most recent use**  โดยไปเซตที่  System Setting->Desktop and Dock แล้วเลื่อนลงมาล่างสุดเพื่อไป **Disable** "Automatically rearrange Spaces based on most recent use" เพื่อไม่ใช้งาน feature นี้

# Mac-Window-Managers
ถ้าเครื่องไม่ได้ติดตั้ง HomeBrew แนะนำให้ทำก่อน

```bash
brew install --cask iterm2
brew install neovim
brew install ripgrep
brew install node
```

# Install Yabai (for Window Managing) and Skhd (for Keboard Shortcuts)
```bash
brew install koekeishiya/formulae/yabai
brew install koekeishiya/formulae/skhd
```

# Create directory and configuration for Yamai

```bash
cd ~
mkdir .config/yabai
cd .config/yabai

touch yabairc
```

## Add Configuration Options to yabai

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

`yabai --start-service`

# Restart yabai:

`yabai --restart-service`

# Start Skhd

`skhd --start-service`

# Restart skhd:
`skhd --restart-service`

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
ctrl + alt - q : yabai --stop-service
ctrl + alt - s : yabai --start-service
ctrl + alt - r : yabai --restart-service
````

# Stop/Start/Restart Yabai
```bash
# stop/start/restart yabai
ctrl + alt - q : yabai --stop-service
ctrl + alt - s : yabai --start-service
ctrl + alt - r : yabai --restart-service
```

# ทดสอบเปิดมาหลายหน้าต่าง เราจะใช้ iTerm2 เพื่อทดสอบ
1. เราเปิด หน้าต่างใหม่ได้โดยการกดปุ่ม **Control+N**
2. กดปุ่ม **Option+N** ที่คีย์บอร์ดเพื่อ move cursor ไปทำงานหน้าต่างย่อยๆที่เปิด (ให้ดูใน configuration skhd อีกทึถ้าจำคำสั่งไม่ได้)
