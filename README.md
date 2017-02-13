# Cumulus
A SoundCloud player that lives in your menubar.

[![GitHub release](https://img.shields.io/badge/download-latest-blue.svg)](https://github.com/gillesdemey/Cumulus/releases/latest)

![screen shot 2015-11-08 at 01 48 24](https://cloud.githubusercontent.com/assets/868844/11018153/de01bade-85ba-11e5-84b4-73299530960b.png)

# Installing

Download the [latest release for OSX](https://github.com/gillesdemey/Cumulus/releases/latest).

*IntelliJ users be warned: This app hijacks the ⌘+Alt+L shortcurt used by IntelliJ to reformat code. See [#40](https://github.com/gillesdemey/Cumulus/issues/40#issuecomment-261022368) and [#77](https://github.com/gillesdemey/Cumulus/issues/77).*

# Developing

## Install dependencies
`npm install`

`npm install -g electron`

## Compile the application
`grunt` or `grunt build`

You can also run `grunt build-linux` to compile the application for Linux, but
there is a lot of chance that it doesn't work on your distro. *(Known to work
on Lubuntu 16.10, see notes below for more insight on how to integrate it)*

## Run the application with the [Chrome DevTools](https://developer.chrome.com/devtools)
`NODE_ENV=development electron .`

### Or in Windows:
- PowerShell: `$env:NODE_ENV="development"; electron .`
- CMD: `set "NODE_ENV=development" & electron .`

## Notes for Lubuntu

After building the app, copy the build inside `dist/` to
`$HOME/.local/lib/Cumulus`.  Open `Cumulus.desktop` inside your favorite editor
and change the text to your username where `<CHANGEME>` is written. Save the
modified file to `$HOME/.local/share/applications/Cumulus.desktop`.  Last step,
soft link `$HOME/.local/lib/Cumulus/Cumulus` to your `$HOME/.local/bin` folder.

You're done!

The `.desktop` file enables Cumulus to be seen inside app menus and launchers.

Here are the commands corresponding to the previous instructions:

    mkdir -vp $HOME/.local/{bin,lib,share/applications}
    cp -vr dist/Cumulus-linux-x64 $HOME/.local/lib/Cumulus
    sed "s/<CHANGEME>/$USER/" Cumulus.desktop > $HOME/.local/share/applications/Cumulus.desktop
    ln -vs $HOME/.local/{lib/Cumulus/Cumulus,bin/Cumulus}
