## About

XIPivot is an addon that allows to dynamically override parts of the DAT files
of your FFXI client without touching the actual files (just like Dats but with extras).

It provides support for multiple overlay directories as well as runtime controls
of which overlays are loaded and used by the game.

The goals behind XIPivot are simple:

- no modifications to the original DAT files
- no more huge folder with thousands of anonymous DAT files
- the ability to sort Mods into separate folders for each mod
- the ability to control which Mods take precedence

## Setup

- 1) Copy the `XIPivot.dll` and the `DATs` folder into Ashita's `plugins/` directory.
- 2) Copy `XIPivot.sample.xml` to Ashita's `config/` directory and rename it to `XIPivot.xml`
- 3) Create a subdirectory inside the `DATs/` folder for each overlay you want to use
- 4) Edit `XIPivot.xml`:
   - add the directory names from 3) for each overlay that should be enabled, separated by comma ','
   - *order matters* - overlays will be used in order, with the first hit for a file being used.
- 5) Add `/load xipivot` as the first line to your setup script (before any /wait or other lines)

### Example - XI-View, XI-Vision and Ammelia's HD-Remake:

Directory structure:

```
<Ashita Install>
   +-- config/
   |    +-- XIPivot.xml
   |
   +-- plugins/
        +-- XIPivot.dll
        +-- DATs/
             +-- README.txt
             +-- XI-View/
             |    +-- ROM/
             |
             +-- XI-Vision/
             |    +-- ROM/
             |    +-- ROM2/
             |    +-- ROM3/
             |    +-- ROM4/
             |    +-- ROM4/
             |
             +-- FFXI-HD/
                  +-- ROM/
                  +-- ROM2/
                  +-- ROM3/
```

XIPivot.xml:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings>
    <setting name="overlays">XI-Vision,XI-View,FFXI-HD</setting>
    <setting name="enabled">true</setting>
</settings>
```

XIPivot defaults to look for your overlays inside the `DATs/` directory next to the `XIPivot.dll`.
If you prefer a different path you can add the key `'root_path'` to `XIPivot.xml` like so:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings>
    <setting name="root_path">C:/my/awesome/addons</setting>
    <setting name="overlays">XI-Vision,XI-View,FFXI-HD</setting>
    <setting name="enabled">true</setting>
</settings>
```

This instructs to XIPivot to search for overlays inside `"C:\my\awesome\addons"` instead.

## In-Game commands

XIPivot makes the in-game command `/pivot` available to load and unload overlays at runtime.
The following parameters are supported:

- a/add overlay_path     -- will load 'overlay_name' as last entry to the overlay list
- r/remove overlay_path  -- will unload 'overlay_name' and remove it from the overlay list
- s/status               -- dumps XIPivot's global status and the list of active overlays
- h/help                 -- print this text

These commands all support a short first letter version (a/r/s/h).
Changes made with add / remove will be reflected in `XIPivot.xml`.

Please note that adding and removing overlays way after the game launches can have side effects.
XI will load some DAT files right at the start and then never look at them again (some menu and landscape textures)
other DAT files are loaded on-demand and overlay changes are visible once that happens (maps, some menu icons, Mog House and a few other locations)

## Limitations

Currently none known

## Disclaimer

I tested XIPivot to the best of my capabilities but I can not guarantee that it works without bugs for 100% of the time.
Use at your own discretion, I take no responsibility for any client crashes or data loss.