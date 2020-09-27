<h6>Introduction</h6>
------------------------------------------------------------------------------------------------------------------------------------------------------------<br/>
lemon is an installer for Arch Linux that can in theory clone just about any Arch installation (or install a completely fresh one!).<br/>
pacman can be used to generate a list of all repository packages installed on any given system, which can then be used as a packagelist for lemon.<br/>
aur packages are not presently supported, but will be coming in the future.<br/>
<br/>
<br/>
<h6>Instructions</h6>
-----------------------------------------------------------------------------------------------------------------------------------------------------------<br/>
**step 1:** clone this repository into any directory **on a running Arch Linux installation ISO** <br/>
    git clone https://github.com/m1ndflay3r/lemon
<br/>
-
<br/>
**step 2:** give lemon execute permissions <br/>
    chmod 755 /path/to/lemon/directory/lemon
<br/>
-
<br/>
**step 3:** either manually write a packagelist **with each package on its own line**, or use pacman to generate a list on an existing installation (recommended). <br/>
    pacman -Qqe > packagelist
<br/>
If you generate a packagelist from a preexisting system, you will need to manually copy it to the **lists** folder within lemon on the arch install iso. <br/>
-
<br/>
**step 4:** create a servicelist containing every service you would like enabled during installation, **with each service on its own line.**<br/>
<br/>
  **eg:**<br/>
    cd lemon<br/>
    echo "ssh" >> lists/servicelist<br/>
    echo "lightdm" >> lists/servicelist<br/>
    echo "NetworkManager" >> lists/servicelist<br/>
-
<br/>
**step 5:** edit lemon.conf and adjust any flags you require (things like grub, refind, multilib usage, etc)<br/>
Note that there are certain behaviors that interact with eachother, for example disabling root will automatically enable non-root user regardless of its explicit setting. <br/>
These interactions will only ever serve to make sure a working system is present at the end of the install.<br/>
<br/>
Full information on each flag and its usage can be found in the comments inside lemon.conf.<br/>
-
<br/>
**step 6:** Launch lemon and begin the installation!<br/>
    ./path/to/lemon/directory/lemon
<br/>

