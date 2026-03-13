# Tips and Tricks for Windows users new to macOS 

## Settings

Desktop & Dock

- Enable "minimize windows to application icon"
- Reduce the size of the dock
- Auto hide/show the dock

Menu bar

- Clock - date/time only
- unselect Spotlight
- select weather

Keyboard

Prefer that the keyboard defaults to function keys, good for vs code etc

- Keyboard -> keyboard shortcuts -> Function Keys -> enable use function keys
- Tips: 
    - MacBook keyboard has no backspace key, simply press and hold fn key and press delete key for Windows backspace equivalent.
    - cmd + spacebar to open spotlight, 99% of time I'll open apps with this combo.

Mouse direction

For Windows users here are some tips esp if using both Windows and macOS and frustrated with macOS scrolling direction.

Mouse

- Set natural scrolling, but this does provide odd behaviour for trackpad
- best solution is if you have a logitech mouse is to set perferred scrolling direction if you are coming from Windows
    - [Logi Options+](https://www.logitech.com/en-au/software/options.html)
- Note, for Windows users not using Logitech mouse, there is a stand along util for overriding std macOS behaviour.

## Finder

From the view menu

- Show toolbar
- Show path bar
- show status bar

### Adding short cuts to Finder

In Windows you'd add an Open With option in File Explorer, on macOS add an app to the Finder Menu then drag file/folder to app icon, simple and fast.

Add VS Code to Finder tool bar, then just drag a folder/file to the VS Code icon and it will open the target folder/file.

- Install VS Code
- In finder/Applications, hold VS Code icon and drag to Finder tool bar

### Disable tags in the Finder folder

Never use them, disable from Finder -> Settings ->Sidebar -> disable recent tags

## Window Navigation

- On Windows everything is an app and <kbd>Windows Tab</kbd>
- On macOS (and Ubuntu and Mint) you have the concept of Apps and Windows.
    - Apps can have multiple windows, eg VS Code you have an instance of VS Code running and multiple Windows (projects) open. 
    - To navigate between multiple windows of the same app - <kbd>use cmd + ~</kbd>. Super efficient way to navigate between windows or the same app like VS Code, Word etc.
- Snap Windows - hold the Option key and drag Window to left or right and release.
- You can resize snapped windows by grabbing slicer between windows and deragging to resize both snapped windows.
- For Windows Powertoys equivalent windows management then use [Magnet](https://apps.apple.com/au/app/magnet/id441258766?mt=12
Magnet) from the App Store or open source/free [Rectangle](https://github.com/rxhanson/Rectangle) 


### Minimize and Maximize windows

As tempting as it seems to use the minimize icon on an app, you are better to hide an app with <kbd>cmd+h</kbd> as it plays better with the <kbd>cmd+tab</kbd> app selector.


### Search scope

Finder -> Settings -> Advanced -> Search in current folder

### New finder windows

- I keep source in a folder names "GitHub" and mostly want to open that Folder when opening Finder.
- Finder -> Settings -> General -> Select your preferred folder


## Install Docker Desktop

Install [Install Docker Desktop on Mac](https://docs.docker.com/desktop/setup/install/mac-install/), be sure to choose Apple Silion. Note, when you install you also be prommpted to install Rosetta for x64 emulation.

## Running Local LLMs

- Ollama or LM Studio
- LM Studio allow you to run MLX optimised models, some 20% faster than GGUF models. So preferred.

## Utilites

### Flycut 

- [Flycut](https://apps.apple.com/au/app/flycut-clipboard-manager/id442160987?mt=12
Flycut (Clipboard manager)) Clipboard manager - better/more accessible than built in Tahoe clipboartd manager.

    - You'll need to add Flycut to the Settings -> Accessibility app list
    - Customise flycut icon. Flycut -> preferences -> appearance -> White scissors
    - Usage tips: Cmd + c to copy, shift + cmd + v to cycle through clipboard history.

### Screen copy

There is a macOS screenshot utility but prefer [Teampaper: Screen recorder](https://apps.apple.com/au/app/teampaper-screen-recorder/id1199502670?mt=12
Teampaper: Screen recorder) as more flex and efficient to use than built in macOS screenshot tools.

For Windows users map the screen shot shortcut key to shift+cmd+s

Set the following options:

- Teampaper -> Settings -> hold shift+cmd+s
- Teampaper -> Settings -> Open at Mac startup


### Monitor Control

For controlling non-Apple monitors from macOS install MonitorControl, its equivalent to Twinkle from the Windows App Store.

- Full fat version from [MonitorControl](https://github.com/MonitorControl/MonitorControl) with support for both screen brightness and monitor volume control. Download the .dmg and install.
- App store for just monitor brightness [MonitorControl Lite](https://apps.apple.com/au/app/monitorcontrol-lite/id1595464182?mt=12
MonitorControl Lite)

## Understanding Auto Started Apps

From system settings-> General -> Login Items and Extensions. For starters ensure following apps auto started

- Flycut
- Teampaper

## Terminal

Terminal is customizable, I normally mode closing window behaviour to "close if the shell existed cleanly"

- Terminal -> Settings -> Shell -> When the shell exits and select desired behaviour.

