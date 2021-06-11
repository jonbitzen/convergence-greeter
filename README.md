# Convergence Greeter

[![Translation status](https://l10n.elementary.io/widgets/desktop/-/greeter/svg-badge.svg)](https://l10n.elementary.io/engage/desktop/?utm_source=widget)

![Screenshot](data/screenshot.png?raw=true)

## Convergence Greeter
This project is a fork of the Pantheon Greeter for ElementaryOS

## Building and Installation

You'll need the following dependencies:

* gnome-settings-daemon >= 3.27
* libaccountsservice-dev
* libgdk-pixbuf2.0-dev
* libgranite-dev >= 5.2.3
* libgtk-3-dev
* liblightdm-gobject-1-dev
* libmutter
* libwingpanel-2.0-dev
* libx11-dev
* meson
* valac

Run `meson` to configure the build environment and then `ninja` to build

    meson build --prefix=/usr
    cd build
    ninja

To install, use `ninja install`

    sudo ninja install

## Testing & Debugging

### Xephyr

Run LightDM in test mode with Xephyr:

    lightdm --test-mode --debug

You can then find the debug log in `~/.cache/lightdm/log`

### VirtualBox

Probably the most productive way to iterate on changes to the greeter is to run it in a virtual machine, while editing it on the host.  To do this:

- Install LinuxMint 20 on a VM in VirtualBox
- Share the convergence greeter source folder from your host machine to your guest OS in VirtualBox.  There is an option for this in the VirtualBox UI.
- On the guest OS, run the command `sudo usermod -aG vboxsf $(whoami)`.  This will give you write permissions to the shared host folder while working on the guest OS.  You may need to log out and back in again for this setting to take effect.

Once the folder is shared and accessible from the guest, you can follow the build instructions with the convergence-greeter to build the greeter on the guest OS.  You can install your IDE of choice on the host and edit from there, but rebuild and restart the greeter over a terminal from the host machine.  See the convenience scripts contained the `test` directory:

- rebuild: rebuilds from source and installs the newly built greeter
- restart: kills the current convergence-greeter, which causes an automatic restart
- set-greeter: allows commands for "test" to set the convergence-greeter as the default greeter, or "slick-greeter" to restore the default greeter

It may be off additional assistance to setup passwordless sudo on the guest OS, and to setup passwordless ssh from the host to the guest.  Also remember that you can checkpoint the guest OS easily, to create convenient restore points if some change made while working on the greeter disables the OS.


