# SiliTune - the CPU Power Manager

**WARNING: Use as your own risk. Get prepared to see your laptop on fire or freeze.**

You want your laptop CPU works like a beast when your program is being run, and consume as less power as possible when you are on battery just browsing the net. You don't want to open a terminal and type a long command just to disable turbo boost. 

With this program, you can control your CPU with just a click of mouse, and automatically switch management profiles when power cable disconnected/connected. 

Functions to be developed:

- [x] Enable/disable turbo boost
- [x] Turn on/off CPU cores
- [x] Undervolting (by `intel-undervolt`)
- [ ] TDP level configuration (by `intel-undervolt`)
- [x] Auto switch profile, ~~handle ACPI events~~, continuous check (per certain seconds) for whether laptop is on AC or battery
- [x] Easy TLP/~~PowerTOP(May cause USB mouse stop responding)~~ toggle
- [ ] Power consumption monitor, temperature/frequency monitor
- [ ] Easy installation
- [x] App launcher, ~~auto start~~(depends on desktop environment)
- [x] system tray icon for easy access and hide

This project uses `intel-undervolt` and it's configuration file for undervolting and TDP control, `intel-undervolt` is available in AUR.

## A Partial Usage Guide

#### **Dependencies**

The program is written in PyQt5, so you may need to install the python3 PyQt5 libraries. 

Undervolting functions depends on `intel-undervolt` module to work, which is available in AUR if you are using ArchLinux. 

#### **Configure files**

`/etc/silitune/sili.conf` is the place of the main configure file used by silitune, an example can be found at `./sili.conf.example`. The meanings of entries in the file is obvious. The program, instead of you, will deal with it. In most cases you don't need to edit it by yourself. 

But if you want to use the undervolting functions, then you should set `uv enabled = 1` in the `global` section in the configure file manually. 

#### **Launcher**

Modify `SiliTune.desktop`, change two `/home/petergu/MyHome/Working/SiliTune/` to the directory you cloned the project.

Run `sudo cp SiliTune.desktop /usr/share/applications/` to place the launcher.

Now you can find the launcher where you find all your other applications. Launch it, enter your user's password, and you can see the program running. 

Close the terminal in which you entered your password, and enjoy. 

DO NOT let the program auto launch in you desktop environment's settings, I encountered some problems when doing so. 

####  **Usage**

The GUI is quite simple to use. 

First, click Help and read it. 

If you don't know the meanings of buttons, like "What's turbo boost?", or "Whether should I change system agent", then you'd better look up before tweaking these buttons. 

**Options, and Save**

Changed options will have effects immediately(except undervolting settings), but only after pressing `Save config` will those changes written into configure file, or they;ll be discarded after quit. 

Power and Battery profiles are not saved simultaneously, so pressing the save button when on power profile will only save your power profile, and vise versa. Considering the mechanism of the program, it's nature to behave like this. 

As an incorrect undervolting may cause system failure, only after pressing the Apply Undervolt button will the undervolting settings be truly written into system. Check twice before press it. 

**Real Real Values**

If you entered an illegal value, or some buttons or options failed to work, the value on the panel will be the (bad) value your assigned, but actually the system is not modified. Press the read real values button will read the (good) values from system, then set them onto the panel. 

**Logger**

Open logger, and see if anything wrong has happened. 

**Switch Profile**

The power and battery profiles are switched **automatically** when you connect/disconnect the power cable. 

**System Tray**

You can always right click the icon in system tray to hide or show the program, and switch profiles quickly. 