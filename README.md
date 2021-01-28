<h4>Introduction</h4>
------------------------------------------------------------------------------------------------------------------------------------------------------------

*lemon* is an installer for Arch Linux that can in theory clone just about any Arch installation (or install a completely fresh one!). Note that at present only ext4 filesystems are supported for ROOT partition. This will be remedied in future updates.

pacman can be used to generate a list of all repository packages installed on any given system, which can then be used as a packagelist for lemon.

experimental AUR package support has been added, but (though it should work just fine) it's not thoroughly tested - thusly it has been labelled experimental and disabled by default. 

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

   ``` pacman -Qqe > /path/to/lemon/directory/lists/packagelist ```

If you generate a packagelist from a preexisting system, you will need to manually copy it to the **lists** folder within lemon on the arch install iso.


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
<h4>*Optional: AUR packages*</h4>

Experimental AUR package support exists, and can be enabled via the AURPACKAGELIST flag in lemon.conf.

To use this feature, create the file *aurpackagelist* in the same format as a regular package list (but using aur packages, obviously).


*eg:*

   ``` cd /path/to/lemon/directory/ ```
   ``` echo "stress-ng" >> lists/aurpackagelist ```
   ``` echo "wine-staging-git" >> lists/aurpackagelist ```
   


.


*Note: Only vanilla Arch Linux is officially supported. while this may work with arch-based distros such as manjaro, this is not officially supported (and will definitely require tweaking lemon.conf to prevent breakage). Your mileage may vary.*

