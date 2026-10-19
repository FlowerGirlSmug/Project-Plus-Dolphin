# Ontario P+ Dolphin Troubleshooting & Guide

# 3.1.5_04 Update (2512 Dolphin)
In the newest version of Dolphin a new feature called Rush Frame Presentation has been introduced which reduces latency by roughly ~8.33ms! (1/2 P+ Frame). This means different things depending on whether you are playing Offline or Netplaying.

## Netplay
For Netplay the new default buffer is 3, however this still adds no additional latency to the game! What this effectively means is the buffer formula is still Ping / 16 and round up, however 3 buffer should always be used at 48 and below ping. Meaning netplaying someone at 48 and below ping will introduce no additional latency! For further information please see this [Spreadsheet](https://docs.google.com/spreadsheets/d/1dUgQr_K9iI8eWlaw2YCwx_AL0Gk3HpihZfe6cSaCdp0/edit?usp=drive_link) or the [Wiki](https://github.com/FlowerGirlSmug/Project-Plus-Dolphin/wiki) <--- WORK IN PROGRESS

## Offline play
When playing Offline due to the new setting you will be playing at 1/2 a frame less latency compared to console, if you want to make sure your Dolphin practice and Offline CRT practice match as closely as possible be sure to disable the `Rush Frame Presentation` setting in Dolphin when playing Offline. It can be found in Config > Advanced, just be sure to re-enable it for Netplay to reap the benefits online and also keep latency consistent, you can always check if the setting is on or off by seeing if it's checkmarked in the settings. You can change this setting at any time in Dolphin, so whether your in a netplay lobby or already playing you can always check and change the setting if needed.

# Shaders
### *I highly recommend before your first netplay session to open Netplay Launcher.dol offline and let the shaders pre-compile ahead of time*

### This fork of Dolphin comes with 3 changes to the graphics settings that aim to reduce stutters
- "Compile Shaders Before Startup" is defaulted
- "Skip Drawing" shader compilation is defaulted
- A pre-made .uidcache file has been included for both Offline Launcher.dol and Netplay launcher.dol

When starting the game the first time you'll have to wait for Dolphin to fully compile the shaders, however it is worth it as it will **massiveley** deduce stutters, and then never has to be done again *(unless you change gfx backends)*! 
Even on lower end hardware my tests have shown at **MOST** compiling shaders could take 2 minutes, but most of your PC's will handle it much quicker.

.

### Help: My game shows a bright white screen or other really bad graphical glitches
This is what happens when "Skip Drawing" is used in combination with the .uidcache file, BUT without "Compile Shaders Before Startup" enabled. In order to fix this go to the user folder, which you can access by clicking File > Open User Folder in Dolphin. From here click the "Cache" folder and delete the "Shaders" folder. After deleting that folder refer to either workaround #1 or workaround #2 as seen below.

.

### Help: When attempting to pre-compile the shaders Dolphin crashes or something goes wrong
There are two workarounds for this

- Workaround #1: Simply turn off "Compile Shaders Before Startup" and load into the game again. This does mean you will be building the shader cache from scratch but thanks to Skip Drawing there shouldn't be any stutters, however there will be noticeable pop in and graphical glitches.
- Workaround #2: Switch "Skip Drawing" to "Specialized (Default)" in Graphics > General. From here boot into the game and play a few matches vs a CPU, in my tests 3-5 matches should be sufficient. After you can switch back to "Skip Drawing" and should be all set, however if graphical glitches still appear then go back to "Specialized (Default)" and keep playing more until "Skip Drawing" finally stops glitching out. Janky workaround i know....but hey it works ¯\_(ツ)_/¯
- **NOTE: You will have to do this for both Offline and Netplay.dol's as the cache is seperate for them.**
