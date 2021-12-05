<h4>Introduction</h4>
-----------------------------------------------------------------------------------------------------------------------------------------------------------

*lemon* is an installer for Arch Linux that aims to be able to clone just about any Arch installation (or install a completely fresh one!). 

Both ext4 and btrfs are supported at present, and a sensible btrfs subvolume configuration is included. Btrfs can be enabled via lemon.conf. 

pacman can be used to generate a list of all packages installed on any given system, which can then be used as a packagelist for lemon. AUR package support is present, and can be toggled via lemon.conf (enabled by default). 

Note: Only systemd is officially supported. While it's technically possible to use other init systems with lemon, it will not configure them for you automatically. As always, YMMV. 
<h4>Instructions</h4>
-----------------------------------------------------------------------------------------------------------------------------------------------------------

<h5>step 1:</h5>

clone this repository into any directory **on a running Arch Linux installation ISO**

   ``` git clone https://github.com/m1ndflay3r/lemon ```


.
<h5>step 2:</h5>

give lemon execute permissions

*(note: the executable lemon, not the lemon folder)*

   ``` chmod 755 /path/to/lemon/directory/lemon ```


.
<h5>step 3:</h5> 

either manually write a packagelist **with each package on its own line**, or use pacman to generate a list on an existing installation (recommended).

   ``` pacman -Qqe | cut -d " " -f1 > /path/to/lemon/directory/lists/packagelist ```

If you generate a packagelist from a preexisting system, you will need to manually copy it to the **lists** folder within lemon on the arch install iso.


Note: If you have any AUR packages installed, they will be added to the auto-generated list as well. In this case, it is highly recommended to enable both AURPACKAGELIST and RETRYASAUR in lemon.conf (both are enabled by default). 


.
<h5>step 4:</h5> 

create a servicelist containing every service you would like enabled during installation, **with each service on its own line.**


*eg:*

   ``` cd /path/to/lemon/directory ```
   
   ``` echo "ssh" >> lists/servicelist ```
   
   ``` echo "lightdm" >> lists/servicelist ```
   
   ``` echo "NetworkManager" >> lists/servicelist ```


.
<h5>step 5:</h5> 

edit lemon.conf and adjust any flags you require (things like grub, refind, multilib usage, etc)

Note that there are certain behaviors that interact with eachother, for example disabling root will automatically enable non-root user regardless of its explicit setting. These interactions will only ever serve to make sure a working system is present at the end of the install.


Full information on each flag and its usage can be found in the comments inside lemon.conf.


.
<h5>step 6:</h5>

Launch lemon and begin the installation!

   ``` ./path/to/lemon/directory/lemon ```


.
<h4><i>Optional: AUR packages</i></h4>

AUR package support exists, and can be toggled via the AURPACKAGELIST flag in lemon.conf (enabled by default).

To use this feature, create the file *aurpackagelist* in the same format as a regular packagelist (but using aur packages, obviously).


*eg:*

   ``` cd /path/to/lemon/directory/ ```
   
   ``` echo "stress-ng" >> lists/aurpackagelist ```
   
   ``` echo "wine-staging-git" >> lists/aurpackagelist ```
   


.
<h5><i>Optional: post install scripts</i></h5>

Post install scripts can be added to lemon/postinstall, and will be executed at the very end of the install before exiting the chroot step. 

This feature can be enabled via the POSTINSTALLSCRIPTS flag in lemon.conf.



*Note: Only vanilla Arch Linux is officially supported. while this may work with arch-based distros such as manjaro, this is not officially supported (and will definitely require tweaking lemon.conf to prevent breakage). Your mileage may vary.*

