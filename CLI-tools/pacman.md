Pacman assignments
==================
These assignments are designed to help you overcome some problems that are
common when using arch's package management system, `pacman`.


1. Create a script file (e.g. "~/bin/uninstaller.sh") that will
   uninstall programmes, their dependencies and configuration files
   from pacman.
   * HINT:  the command to put in the script will begin with `pacman -R`
   * HINT2: pacman supports syntax like the following `pacman -R -h` to get
            help for the '-R' switch.
2. Find out how to clear the pacman cache and describe why you'd ever want to
   issue such a command<
   * HINT: Find out the main switch to use in pacman for the installed packaged database
   * HINT2: same as in 1.
   * HINT3: the answer to the first hint is -Q
3. Download a package through pacman, without installing it
4. Inspect the package contents. Specifically, inspect the files `PKGBUILD` and
   `install`, which define what happens, when pacman installs this package.<br/>
   `PKGBUILD` defines build process<br/>
   `install` moves the files that result from the build to the correct paths
   (notably, it moves (or symlinks) the executable to /usr/bin).
   * HINT: pacman packages end in (their file-extension is) ".xf.tar.gz" that is,
         they are actually 'just' so-called "tarballs," which can be extracted
         with standard tools (`man tar`).
5. Install the inspected package
   * HINT: it's done with the command `makepkg -sri` but what do those switches
     do?
   * TROUBESHOOTING HELP:
    ** did you run `makepkg` as root? (it will tell you not to, if you did)<br/>
        So, you know, ....__don't__.<br/>
    ** did it complain about missing packages/dependencies?<br/>
        Try installing those normally with `pacman`, if that fails: either 1)
        read up on AUR (see below) or 2) delete the (still uninstalled) package
        folder and downloaded package and choose another one (with fewer/other
        dependencies).
6. ADVANCED/UNNECESSARY/NICE-TO-HAVE:<br/>
   Read about the AUR (https://wiki.archlinux.org/index.php/Arch_User_Repository)
   and try to download+install a package from it (any package will do, since
   you can always uninstall with your script from no. 1.).
   Beware that it is good customs to do no. 4 _WHENEVER_ installing packages
   that have not been released in the official pacman repositories.
   The reason for this being that a malicious packager can make the
   build scripts do practically anything a root user can do to your system.
7. UNNECESSARY/NICE-TO-HAVE:<br/>
   If you want easier access to the AUR, there exist various frontends
   for this. One such frontend is `yaourt`, which allows you to search
   and install directly from the AUR, as well as being a wrapper script[1]
   around pacman, so that it may completely take over the role of package manager.

[1] "wrapper scripts" aim to extend the functionality of the programme
they wrap. If for instance you feel that skype should have a -u option
(dunno if it already does), you would create a wrapper script that handled
that single switch, while 'simply' passing everything else on to the actual skype command.
