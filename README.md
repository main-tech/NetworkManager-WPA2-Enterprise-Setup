# NetworkManager-WPA2-Enterprise-Setup
How to set up NetworkManager for use on school and other WPA2-Enterprise Networks using only systemctl, and the text editor of your choice.

# Backstory
Ever since moving off of ubuntu, network setup has been a pain, so here's a how-to and skeleton for a config file for WPA2 Enterprise Networks. This method has been tested on two different university networks and worked for both.

# How To
0. If you don't have NetworkManager installed, either get it from your package manager, or transfer the source from a computer that has network access and go [here](http://www.linuxfromscratch.org/blfs/view/svn/basicnet/networkmanager.html) for instructions on how to install it.
1. Generate a UUID with `uuidgen`
1. Copy the base config from this repository into `/etc/NetworkManager/system-connections/[CONNECTION-NAME]` and edit in the connection id with your favorite text editor
1. Change the following fields:

   - `uuid` (generated by `uuidgen`)
   - `ssid`
   - `identity` (user id or username, usually given to you by the school)
   - `password`
   - If you know that your network has different authentication methods, change those here as well.

1. Write and save the file, then run

   ```bash
   chown root /etc/NetworkManager/system-connections/[CONNECTION-NAME] && \
   chmod 600 /etc/NetworkManager/system-connections/[CONNECTION-NAME]
   ```

8. Restart the NetworkManager service with `sudo systemctl restart NetworkManager`

With that you should have a functioning wifi connection on WPA2-Enterprise!
