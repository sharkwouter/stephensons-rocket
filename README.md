# steamos-installer

Stephenson's Rocket - a modified SteamOS installer, with wider support for more complex computers

# The Artist Formerly Known As Ye Olde SteamOSe

SteamOS is now shipping, in beta form at least, and it's all cool and stuff.

Valve have now integrated most of the improvements from Ye Olde SteamOSe, such as BIOS and DVD support, into their installer. You can download it from [here](http://repo.steampowered.com/download/SteamOSDVD.iso).

Stephenson's Rocket replaces the Ye Olde SteamOSe project by building back on Valve's installer with bug fixes and improvements - especially hardware support.

This kind of collaborative development demonstrates the power of Open Source - and remember, you can contribute to Stephenson's Rocket too! Click "View on GitHub" at the top of the screen to get started, and watch the development tutorial video linked below!

# Improvements

- SteamOS monopolizes drives. Stephenson's Rocket can resize NTFS partitions.
- SteamOS only supports basic partitions. Stephenson's Rocket supports LVM and RAID.
- SteamOS requires a Radeon 5000 or newer for ATI users. Stephenson's Rocket will use the Open Source driver instead on older cards.
- SteamOS requires a Geforce 400 or newer for NVIDIA users. Stephenson's Rocket will use the legacy 340 series driver instead on older cards.
- SteamOS is only updated when Valve have time. Stephenson's Rocket comes with the tools to update it with the latest stuff yourself!

![SteamOS on VMware](http://i.imgur.com/a3jnZ6r.png)

# Planned improvements

- Support NVIDIA cards no longer supported in current nvidia-glx driver.

# How to install?

A DVD image is always available at http://stephensonsrocket.horse/

To get started, download the torrent.

Otherwise, clone this repo, and run `./gen.sh`.

## Installing from a DVD

Just burn the ISO to a blank DVD from your favourite tool, and boot it.

## Installing from USB (Mac)

Open a Terminal window from the Utilities section of Applications.

Type `diskutil list` to get a list of devices - one of them will be your USB stick (e.g. `/dev/disk2`). Follow the Linux instructions below but change:

* `/dev/sdX` to `/dev/rdiskX`
* `bs=1M` to `bs=1m`

## Installing from USB (Linux)

Plug in the USB stick and run `dmesg`; look for a line similar to this:

    [377039.485179] sd 7:0:0:0: [sdc] Attached SCSI removable disk

In this case, `sdc` is the device name for the USB stick you just inserted. Now we put the installer on the stick, as root (e.g. use `sudo`) run 

    dd bs=1M if=/path/to/rocket.iso of=/dev/sdX 
    
sdX should be the USB stick device from the information you received from `dmesg`. Be sure to use sdX, not sdX1 or sdX2. Then boot into the stick.

## Installing from USB (Windows)

Download [Win32 Disk Imager](http://sourceforge.net/projects/win32diskimager/) and use it to copy the .iso to your USB stick (1GB minimum size).

## Once the installer is up...

Pick the "Automatic Install" option to wipe the first hard disk in your system and install SteamOS to it.

For more sophisticated booting - e.g. dual-boot or custom partition sizes - select the "Expert" option. Use of this mode is documented in the support video [here](https://www.youtube.com/watch?v=3MjkfMs-4T4).

Beyond that, just follow Valve's instructions from [their site](http://store.steampowered.com/steamos/buildyourown) - Stephenson's Rocket should behave exactly like the real SteamOS, except it works on more systems

## Updating

Before you generate a new image you need to ensure that your pull is up to date as things change quickly:

- `git pull` in the steamos-installer directory will ensure you have the latest code.
- `./gen.sh -d` will ensure that you download the latest SteamOSDVD.iso

# Known issues and workarounds

- 3D support is broken in Big Picture Mode itself and in 32-bit games in VirtualBox. This is a flaw in the Debian packaging of the VirtualBox guest drivers.
- Crashes and strange behaviours on NVIDIA Maxwell cards with certain OpenGL games and applications. This requires an update to the lastest driver to fix, which has not yet been packaged for APT.

# How can I help?

Test it and report back to #steamos on Freenode

Or support me by donating - Donate via [PayPal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=888397), [Steam](http://steamcommunity.com/id/directhex/wishlist), or [Amazon](http://www.amazon.co.uk/wishlist/LN9AGFCAGAHR). Donations will be used to help with testing - wifi adapters, hard disks, graphics cards, etc.

# Special Thanks

- Wouter Wijsman (shark) for his continued contributions.
- Kevin van de Pas (St.Jimmy) for his continued contributions.
- Michael Waltz (ecliptik) for his continued contributions.
- Anonymized benefactors for their sponsorship (~400 day VMware key; £60; 1 month reddit Gold; Shoot Many Robots game; Civ5 gold upgrade).
- Various Valve engineers for their help.
- steam-scene.com for awarding the top prize in their SteamOS modding contest to Ye Olde SteamOSe
- Valve Software for their kind donation of a Steam Controller prototype
- Collabora Ltd for their kind donation of 2 x 500GB hard disks for testing
