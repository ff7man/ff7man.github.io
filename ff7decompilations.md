# FF7 Decompilations

Parts of FF7 have been decompiled by https://github.com/ergonomy-joe, this is a quick guide to compile and execute his projects.

## Compiling

Starting from Windows 10

1. Install [FF7 1998](https://archive.org/details/FinalFantasyVIIUSA) and choose maximum install

Mount the iso using virtual clone drive and install to `C:\ff7`

2. Install [FFNx](https://github.com/julianxhokaxhiu/FFNx)

Unzip the archive into `C:\ff7` and run the .reg file. 

3. Install [Visual Studio 2008](https://archive.org/details/dev-microsoft-visual-studio-2005-2015-Pro)

Mount the iso using virtual clone drive and run the installer

4. Download [Direct X 5 SDK](https://archive.org/details/idx5sdk)

Run the installer to unzip to C:\dx5sdk

5. Download one or all of ergonomy-joe's projects

- [ff7-coaster](https://github.com/ergonomy-joe/ff7-coaster)
- [ff7-worldmap](https://github.com/ergonomy-joe/ff7-worldmap)
- [ff7-chocobo](https://github.com/ergonomy-joe/ff7-chocobo)

6. Unzip his projects and update the .vcproj 
The vcproj file reference `\VC50PROCD1\DXSDK5` change this to `C:\dx5sdk\` throughout

7. Open the .sln in visual studio 2008 and build the project

8. Reduce the color mode to 16bit on the exe

Right click the exe -> Properties -> Compatibility -> Reduced Color mode 16 bit

My github forks contain precompiled binaries.

## FF7 Coaster

Double click the exe to run

Movement:
- Num lock to enable buttons
- Numpad Enter to Shoot
- Numpad 5 to Pause
- Numpad 4862 to move

![image](https://user-images.githubusercontent.com/116538902/202667387-9c9ebe7d-e7fe-4843-a931-6017f6e7de43.png)
![image](https://user-images.githubusercontent.com/116538902/202667429-9a8945ec-ee97-4528-a37b-06865a04c979.png)


## FF7 Chocobo

- The default save loaded is at C:\ff7\save\save00.ff7
- Double click the exe to run

Movement:
- Num lock to enable buttons
- Numpad 5 to Start race
- Numpad Enter to select tickets
- Numpad 4862 to move
- Numpad - to enable manual mode

Different Compilations:
- The `patch_setChocoboInfo()` function in FF7ChocoboMain.cpp gives various customizations to what type of race you will have

![image](https://user-images.githubusercontent.com/116538902/202667599-f120a6a7-6688-4d29-8c0d-1226a247809c.png)
![image](https://user-images.githubusercontent.com/116538902/202667745-3b539266-cbd3-40b8-9774-07f95f67fcf3.png)
![image](https://user-images.githubusercontent.com/116538902/202668320-b7f704b3-e0ba-435e-a943-231f7b96f015.png)
![image](https://user-images.githubusercontent.com/116538902/202668503-976e4b49-82d1-4f53-97de-a91170137c79.png)


## FF7 Worldmap

- The default save is C:\ff7\save\save00.ff7 slot 1 (second save), this should be on the world map not in an area.
- Double click the exe to run
- Battles reset world map
- New areas reset world map

# Movement:
- Numpad 4862 to move
- Numpad - map
- Numpad + Menu
- Numpad 0 Exit Menu

![image](https://user-images.githubusercontent.com/116538902/202671954-c14be444-3ada-4e8e-a4ca-45306618f4ad.png)
![image](https://user-images.githubusercontent.com/116538902/202672044-3a242b59-b6b1-4a8b-866e-350a0f1542b3.png)
![image](https://user-images.githubusercontent.com/116538902/202672649-688f1199-f52d-4316-9909-e95017a6f1d2.png)

While still dark, text shows up better when not using VMware Workstation
![image](https://user-images.githubusercontent.com/116538902/202673687-6ade5523-f602-4f7b-8c0a-c3e326c5e1a6.png)
