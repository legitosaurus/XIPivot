## About

XIPivot is an addon that allows to dynamically override parts of the DAT files
of your FFXI client without touching the actual files.

It provides support for multiple overlay directories as well as runtime controls
of which overlays are loaded and used by the game.

The goals behind XIPivot are simple:

- no modifications to the original DAT files
- no more huge folder with thousands of anonymous DAT files
- the ability to sort Mods into separate folders for each mod
- the ability to control which Mods take precedence

## Compatibility

XIPivot works together with [Ashita v3](https://www.ashitaxi.com) as well as [Windower 4](http://www.windower.net).

## Installation

- Head over to the [Releases page](https://github.com/Shirk/XIPivot/releases) and pick the ZIP that matches your launcher
- Follow the README.md inside the archive  for setup and configuration instructions

## Modifications / Contribution

If you would like to build XIPivot from source you need the Visual Studio 2017.
The Community Edition is available for free from [Microsoft](https://visualstudio.microsoft.com/vs/community/).

Otherwise it's just these three steps:

- clone the repository
- open the solution
- chose "Build -> Rebuild Solution" .

The addon and plugin versions will be placed inside the directory `build\Release\Windower` and `build\Release\Ashita`.

**NOTE: Chose "no" if Visual Studio offers to upgrade the project elements to Windows 10 SDK targets **

## Disclaimer

I tested XIPivot to the best of my capabilities but I can not guarantee that it works without bugs for 100% of the time.
Use at your own discretion, I take no responsibility for any client crashes or data loss.