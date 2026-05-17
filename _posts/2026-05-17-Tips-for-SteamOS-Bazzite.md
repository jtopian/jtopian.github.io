---
title: JT's Tips for SteamDeck/SteamOS/Bazzite
date: 2026-05-17 09:00:00 -0700
categories: [Tutorials, Linux]
tags: [linux, flatpak, steam]
---

## Linux Software
On an immutable distro like SteamOS or Bazzite, a lot of your software is going to come from the Discover store. This installs apps using a system called Flatpak, which isolates each app in a container separated from the rest of the system. You have to grant permissions similar to an Android/iOS app. So grab [Flatseal](appstream:com.github.tchx84.Flatseal) from Discover, it's used for managing those permissions. Most apps won't need any adjustments, but if you need to grant access to a folder, or your webcam or something, it'll be in there.

There's lots of free games and apps in Discover, take some time to browse through the different categories in there, you'll find some interesting stuff.

If you end up adding something even more custom, you can create a `*.desktop` file in `~/.local/share/applications` to have it show up in your App menu. From there, it can be added to Steam as a Non-Steam game to give you a seamless console experience.

### SteamGridDB
If you add software through Discover or manually with a `*.desktop` file, you can also add them to your Steam library so that it shows up in the "Non-Steam" tab in big picture mode. You can add cover art to non-Steam software using [SGDBoop](https://www.steamgriddb.com/boop), allowing you to easily add art through [SteamGridDB](https://www.steamgriddb.com/).

## Non-Steam Launchers
- **Lutris** also gives access to Epic, GOG, Amazon, EA, Ubisoft, and others, including an option to "Add a windows game from an executable" where it will poll its own database to find out the best way to run it. I have Sim City 2000 and Sim Tower that way.
 - [Lutris on Discover](appstream:net.lutris.Lutris) | [Lutris on Flathub](https://flathub.org/en/apps/net.lutris.Lutris)

- **Heroic Games Launcher** gives access to Epic, GOG, and Amazon games.
 - [Heroic Games Launcher on Discover](appstream:com.heroicgameslauncher.hgl) | [Heroic Games Launcher on Flathub](https://flathub.org/en/apps/com.heroicgameslauncher.hgl)

- **Prism Launcher** is a Minecraft Java launcher, that has integrated mod management for multiple frameworks.
 - [Prism on Discover](appstream:org.prismlauncher.PrismLauncher) | [Prism on Flathub](https://flathub.org/en/apps/org.prismlauncher.PrismLauncher)

## Windows software on Linux
Steam has a utility called Proton, which is a customized version of WINE ("WINE Is Not and Emulator") that translates Windows syscalls to Linux on the fly. It's really good nowadays, and is compatible back to ancient times.

Check [**ProtonDB**](https://www.protondb.com/) to see how certain games run on Steamdeck. Comments on each software there will give hints about tweaks for optimizing.

**ProtonUp-Qt** provides an interface for managing proton versions for all of your Steam games.
 - [ProtonUp-Qt on Discover](appstream:net.davidotek.pupgui2) | [ProtonUp-Qt on Flathub](https://flathub.org/en/apps/net.davidotek.pupgui2)

## Linux Utilities
- **Pusleaudio Volume Control** does just what it sounds like.
 - [Pavu on Discover](appstream:org.pulseaudio.pavucontrol) | [Pavu on Flathub](https://flathub.org/en/apps/org.pulseaudio.pavucontrol)

- **Helvum** if you want to peer into the audio stack on Linux, it'll let you reroute audio inputs/outputs. I don't have a ton of need for it, but it has its moments.
 - [Helvum on Discover](appstream:org.pipewire.Helvum) | [Helvum on Flathub](https://flathub.org/en/apps/org.pipewire.Helvum)

## Other Apps
- **Strawberry Music Player** for local music libraries.
 - [Strawberry Music Player on Discover](appstream:org.strawberrymusicplayer.strawberry) | [Strawberry Music Player on Flathub](https://flathub.org/en/apps/org.strawberrymusicplayer.strawberry)

- **VLC** for video.
 - [VLC on Discover](appstream:org.videolan.VLC) | [VLC on Flathub](https://flathub.org/en/apps/org.videolan.VLC)

- **MPV** is another common video player, has a more minimalist feel than VLC.
 - [MPV on Discover](appstream:io.mpv.Mpv) | [MPV on Flathub](https://flathub.org/en/apps/io.mpv.Mpv)

- **Krita** is my personal favorite drawing/image editing app.
 - [Krita on Discover](appstream:org.kde.krita) | [Krita on Flathub](https://flathub.org/en/apps/org.kde.krita)
