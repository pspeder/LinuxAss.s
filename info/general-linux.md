#Command line options (a.k.a. switches or flags)
When you type in a command at the "command line" (or more correctly: "...in a
\*nix shell, such as bash"), often times, it will allow you to control the
application's operation and output by what is known as switches or flags.
A typical example would be to get a short help message about an application's
usage and main flags, which most programs offer:

    cat --help

You will likely experience that the syntax for these flags can differ.
Sometimes you will get full, meaningful flags as the one above, however, other
programmes will use single-letter flags as below:

    lsof -h
    lsof -? # some even provide alternate flags for the operation

...or an combination hereof. Different developers have different reasons for
using their respective syntax. Sometimes the longer names are used to provide
an 'easy-to-remember' alternative to a single-letter switch:

    vim -f          # 'f' for foreground (i.e. don't fork to it's own process)
    vim --nofork    # does the same as above

Yet, other times, it is to extend the number of possible switches

    # The '--progress' does not have a "short version"
    rsync -avz --progress <srcpath> <destpath>
    
    #(rsync is basically a 'cp/mv'-command that also does network transfers)

The programme, lsof, simply has too many options for them to be defined solely
with single-letter switches, even if it still heavily relies on the smaller
amount of typing required by single-letter switches.
Thus, the developers have extended the idea of such switches to utilise the
`+`-sign in addition to `-`

    # lsof extends no. of possible switches by also utilising '+'
    lsof +D /usr/bin

Yet another alternate syntax is the idea of passing "commands" (sometimes:
"modes") to your command:

    systemctl status

...some programmes, though, do not differentiate between such "command line
options," as witnessed by the `man`-page for `route`.

    man route       \# See the "Options"-section

Please note that **I may not have been consistent with my use of these words**.
Sorry 'bout dat.

#pids
`pid` stands for __P__ rocess __ID__ entification and is a unique
number assigned to each running process. These can sometimes be
stored in files, who, then, usually ends in `.pid`.

N.B.: An application may or may not spawn multiple processes per instance,
depending on their complexity (examples of mulitple process applications
could include: threaded applications and applications that call external
libraries). If you use `htop` you can get a tree view indicating which
processes started which other processes.

#The Filesystem Hierachy Standard (FHS)
This is how the filesystem is laid out, when the system is fully mounted.
The FHS is a standard, now in its 3rd iteration, which specifies where all
(types of) files belong on the system. A typical Linux distribution does not
necessarily implement the entire FHS, ArchLinux, for instance, symlinks the
directory /sbin to /usr/sbin (as well as other discrepancies, which is due
to systemd's standards: https://wiki.archlinux.org/index.php/Arch_filesystem_hierarchy)

Recommended reading:
  [1] Concise and detailed, with full overview of FHS' structure
      https://en.wikipedia.org/wiki/Filesystem_Hierachy_Standard


###The most used ones:
Below is an ASCII-'art' tree illustrating, the most interesting of the folders
in your filesystem root ( / ), as defined by me.

```
+-   /              # This is the root of the filesystem. Everything the
|                   #  system knows about is mounted here.
|
+--- /bin           # System-specific binaries
|
+--- /boot          # This contains stuff like bootloader configs, kernel
|                   #  images and the likes
|
+--- /dev           # This contains all the input/output devices connected
|                   #  (both hardware such as: webcam, hdd, cd, etc.; but also
|                   #  'virtual devices' such as /dev/random or /dev/null,
|                   #  which output pretty much, what you would guess
|                   #  (try `cat /dev/random`))
|
+--- /etc           # System-wide configuration files (both for the actual
|                   #  system (see, e.g., /etc/pacman.conf) and for installed
|                   #  applications (such as the ssh daemon (see, e.g.,
|                   #  /etc/ssh/sshd_config))
|
+--- /home          # You should know what is stored here already
|
+--- /media         # Mounting folder for when applications automount
|
+--- /mnt           # Different mounting folder (often used for mounts
|                   #  that will be persistent (external hdds added to
|                   #  /etc/fstab, for instance)
|
+--- /opt           # Installation of (especially proprietary) applications
|                   #  that are either very large (would consume a lot of space
|                   #  in /usr, which could be problematic on some systems),
|                   #  or don't support splitting up installed resources (see
|                   #  the /usr/<subfolder>s for 'proper installations')
|
+--- /proc          # Just a folder. During system uptime it is populated with
|                   #  the running processes' ids and other info for running
|                   #  your system (N.B.: this is NOT a proper filesystem
|                   #  ---do _NOT_ write stuff in there, unless you know
|                   #  exactly what you're doing)
|
+--- /run           # Pretty much the same as above (see [1] for more thorough explanation)
|
+--- /root          # The 'home directory' of the root user
|
+--- /srv           # Storage for files that are "served" (web apps, shares, etc.)
|
+--- /sys           # Again not a proper filesystem, but used by the system
|
+--- /tmp           # This is where you'd generally compile stuff, or do other
|                   #  actions, which require some temporary storage---do _NOT_
|                   #  expect files stored here to be persistent across reboots
|
+--- /usr           # 'Install directory' -- this is where (most) installed apps
 ---
   +-- /usr/bin     # The executables (or symlinks to them) go here
   +-- /usr/include # This folder contains "header" files [2]
   +-- /usr/lib     # Libraries that installed programmes can call upon (python libraries go here, for instance).
   +-- /usr/lib64   # Same as above, only for 64-bit systems (on arch the two
   |                #  are symlinked since naming conventions avoid duplicates)
   +-- /usr/local   # A folder similar in function and layout to /usr, but for
   |                #  apps that were not installed using your package manager.
   +-- /usr/sbin    # 'Secure' binaries. This includes the various shells and
   |                #  other apps that the system need to function properly.
   +-- /usr/share   # Whatever other resources an app might need (images,
   |                #  sounds, man pages, default configurations, etc.)
   +-- /usr/src     # Most package managers will allow you to download the
   |                #  sources for installed packages (pacman does not do this
                    #  by default, hence, this will be empty most of the time)
 ---
+--- /var           # Various files needed by programs during their execution.
|                   #  This might pertain to system-wide caches, lock-files,
|                   #  logs, etc. Pacman uses it to keep track of installed
|                   #  packages etc.
 ---
   +-- /var/tmp     # Is often used for "swap"-files (in this context, take
   |                #  it to mean: temporary storage of introduced changes that have not yet been written (in, for instance, vim))

```
