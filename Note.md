# Package
1. Conky : conky
2. Tilda : tilda
3. Cava : cava
4. WhiskerMenu : xfce4-whiskermenu-plugin
## Fonts
1. Roboto : Manual[Roboto.unzip] (/usr/share/fonts/RobotMono)
2. JetBrains : Manual[JetBrains.unzip] (/usr/share/fonts/JetBrainsMono)
## Themes
1. Ant-Theme : Manual[Ant-Nebula.tar.xz] (/usr/share/themes/Ant-Nebula)
   > Ant-Nebula, Ant-Nebula-alt-style, Ant-Nebula-slim, Ant-Nebula-slim-standart-buttons, Ant-Nebula-standart-buttons
## Icons
1. Tela : Manual[01-Tela.tar.xz] (/usr/share/icons/Tela,Tela-dark,Tela-light)
   > Tela, Tela-dark, Tela-light

# Wallpaper :
- $ sudo mkdir /usr/share/backgrounds/t4n-os
1. My Collection Wallpaper[jpg/png] (/usr/share/backgrounds/t4n-os/*)

# Config-Dotfiles[Template] (/.config/) :
- https://github.com/disws1/xfce-customize
./
├── cava/
│   └── config
├── conky/
│   └── conky.conf
├── gtk-3.0/
│   ├── gtk.css
│   └── settings.ini.bak
├── tilda/
│   └── config_0
└── xfce4/
    └── terminal/
        └── terminalrc

# Panel :
## Panel 1 :
### Display
#### General
- Mode : Horizontal
- Lock Panel : True
- Automically Hide the Panel : Never
- Reserve space on screen edges for the panel : True

#### Measurements
- Row Size(Pixels) : 38
- Number of Rows : 1
- Border Width(Pixels) : 0
- Lenght : 1920
- Automatically increase the Length : True

### Appreance
#### General
- Dark Mode : True
#### Background
- Style : Solid Color
- Color : $000000(A 30)
#### Icons
- Adjust Size Automatically : False
- Fixed Icons Size(Pixels) : 35

#### Opacity
- Enter : 100
- Leave ; 100

### Items
1. Whisker Menu
2. Separator : Style (Transparent - Expand(False))
3. Workspace Switcher
4. Separator : Style (Transparent - Expand(False))
5. Windows Buttons
6. Separator : Style (Transparent - Expand(True))
7. Power Management Plugin
8. Notification Plugin
9. PulseAudio Plugin
10. Clock

## Panel 2 :
### Display
#### General
- Mode : Vertical
- Lock Panel : True
- Automically Hide the Panel : Intelligently
- Reserve space on screen edges for the panel : True

#### Measurements
- Row Size(Pixels) : 60
- Number of Rows : 1
- Border Width(Pixels) : 0
- Lenght : 1
- Automatically increase the Length : True

### Appreance
#### General
- Dark Mode : True
#### Background
- Style : Solid Color
- Color : $000000(A 30)
#### Icons
- Adjust Size Automatically : False
- Fixed Icons Size(Pixels) : 35

#### Opacity
- Enter : 100
- Leave ; 100

### Items
1. Application Finder(Software)
2. Firefox Web Browse(Software)
3. Terminal Emulator(Software)
4. File Manager(Software)
5. Settings Manager(Software)

# Config-Settings
## Whisker Menu
### General
- Show as List(out of the three options)

- Show generic applications name : False
- Show category names : True
- Show application tooltips : True
- Show application descriptions : True

- Appplications icons size : Small
- Category icon size : Smaller

- Menu Width : 450
- Menu Height : 500
- Background Opcaity : 100

### Appearance
#### Menu
- Position Categories Horizontal : False
- Position Categories on Left : True
- Position Profile on Bottom : True
- Position Search Entry on Bottom : False
- Postion Commands Next to Search Entry : False
- Profile : Round Profile

## panel Button
- Display : Icon
- Title :
- Icon ; VoidLinux-NonText.svg
- Use a Single panel row : False

## Workspace
### General
#### layout
- Number of Workspace : 5
#### Names
- 1 - 5 : ◉

### Margins
- Top : 5
- Left : 5
- Right : 5
- Bottom : 45

### Properties(Workspace Switcher)
- Appearance : Buttons
- Number of Rows : 1
- Show Workspace : False
- Switch Workspace using the mouse wheel : True
- Wrap around workspaces : False

## Appearance
### Style
- Ant-Nebula
### Icons
- Tela
### Fonts
- Default Font : JetBrainsMono Nerd Fonts regular 10
- Default Monospcae : JetBrainsMonoNL Nerd Fonts regular 10

## Window Manager
### Style
- Theme : Ant-nebula
- Title Font : JetBrainsMono Nerd Fonts regular 10
- Title Aligment : Left

## Mouse and Toucepad
### Device : Touchpad
#### Touchpad
- Tap touchpad to click : True

## Keyboard
### Application Shorcuts
1. thunar : Super+E
2. xfce4-terminal-whiskermenu : Super L
3. xfce4-screenshooter : Shift+Super+S
4. xfce4-session-logout : Ctrl+Alt+Delete
5. xfce4-terminal : Ctrl+Alt+T
6. xflock4 : Ctrl+Alt+l
7. xkill : Ctrl+Alt+Escape

## Session and Startup
### Add
- Conky
Name : Conky
Desc : Lightweight system monitor for X and Wayland
Command : conky
Trigger : on login
