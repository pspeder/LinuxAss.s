Processes, Opened files and user sessions
=========================================
This file intends to introduce some of the most common tools available when
working with Linux system administration.
An incomplete list of the applications you will/should use to solve these assignments:
* `who`
* `ps`
* `lsof`

...some of these (namely, `ps` and `lsof`) are __beasts__ of commands - they both
have a vast list of command line switches (see below), and a plethora of use
cases, thus, being able to search in `man` pages is of importance (you do that by
typing `/` then your search term, and then press `<ENTER>`, when reading the
`man`-page).

You are advised to read the man page of all commands that are named here.
Specifically, I would recommend reading the "options" and/or "switches" section(s)
of said `man`-pages, as these are key to understanding the operation of such
programmes.


####A note on command line options (a.k.a. switches or flags)
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
    lsof -?

...or an combination hereof. Different developers have different reasons for
using their respective syntax. Sometimes the longer names are used to provide
an 'easy-to-remember' alternative to a single-letter switch:

    vim -f          \# 'f' for foreground (i.e. don't fork to it's own process)
    vim --nofork    \# does the same as above

Yet, other times, it is to extend the number of possible switches

    \# The '--progress' does not have a "short version"
    rsync -avz --progress <srcpath> <destpath>
    
    \#(rsync is basically a 'cp/mv'-command that also does network transfers)

The programme, lsof, simply has too many options for them to be defined solely
with single-letter switches, even if it still heavily relies on the smaller
amount of typing required by single-letter switches.
Thus, the developers have extended the idea of such switches to utilise the
`+`-sign in addition to `-`

    \# lsof extends no. of possible switches by also utilising '+'
    lsof +D /usr/bin

Yet another alternate syntax is the idea of passing "commands" (sometimes:
"modes") to your command:

    systemctl status

...some programmes, though, do not differentiate between such "command line
options," as witnessed by the `man`-page for `route`.

    man route       \# See the "Options"-section

Please note that **I may not have been consistent with my use of these words**.
Sorry 'bout dat.


####pids
`pid` stands for __P__ rocess __ID__ entification and is a unique
number assigned to each running process. These can sometimes be
stored in files, who, then, usually ends in `.pid`.

N.B.: An application may or may not spawn multiple processes per instance,
depending on their complexity (examples of mulitple process applications
could include: threaded applications and applications that call external
libraries). If you use `htop` you can get a tree view indicating which
processes started which other processes.

Assignments
-----------
1. Find out which processes are currently running the system.
  * HINT: This can be done in many ways.
  * HINT2: `ps` can _definately_ do this.

2. Find out which ones where started by you (or by applications, your
   user has opened).
  * HINT: `ps` _can_ do this, but may not be the easiest solution here.
  * HINT2: Try with `lsof`.
  * HINT3: Find out what `lsof -u` means.

  * EXTRA: There are still other ways of doing this - if you feel up for it,
          you _could_ write a script, which search the appropriate file in
          `/proc/*/` and returns the process ids of the ones matching the user.
          This is advanced (and also redundant, since lsof does exactly this),
          so purely an educational exercise.

3. Write a shell script, that will search running processes for the command
   used to invoke them, and return said command along with it's pid.

  * EXTRA: In what common scenario would this* be useful?<br/>
          *) being able to find the pid of a given process name.

4. What is CWD for an application?
  1. Read the "definition"
  2. Determine how to find CWD for a given process (say, 3813 (randomly chosen))
  3. What problems could arise if one started a programme from a different location than the originally intended one?

  * HINT: If the author has used 'relative paths', such as:
          `path/to/some/executablecode.sh` inside the script,
          rather than, for instance:
          `/actual/path/to/some/executablecode.sh`

5. Determine how many virtual terminals (terminal emulator windows) your user
   has open.
  * HINT: use `who`


###Whereto from here?
For now the only other article that has been somewhat thoroughly typed is the
article on the archlinux package manager [pacman](pacman/pacman.md)
<!---
I would suggest the [extended lsof article](lsof/lsof.exercises.md)
and the [extended ps article](ps/ps.exercises.md), to better get to grips
with those two tools.
--->

