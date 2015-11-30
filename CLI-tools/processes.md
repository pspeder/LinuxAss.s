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
cases, thus, being able to search in man pages is of importance (you do that by
typing `/` then your search term, and then press `<ENTER>`, when reading the
man page).

####"command line switches"
...refers to the arguments that begin with `-`, given to commands on the
shell, e.g. the `-a` below:

    ps -a

They are to be seen in contrast to command commands, such as `status` in
the command:

    systemctl status

Some common traits of command line switches:
* When only a single dash, it usually indicates 'single-letter switches'
* 'single-letter switches' can be grouped, as in: `ps -axu`, thus removing
  some of the dashes.
* Most commands provide a `-h` and/or `--help` switch, whose purpose
  should be clear from the context ;-)
  (they display a short help message, usually describing
  command usage, commands and switches). Try, e.g., `git --help`

####pids
`pid` stands for __P__rocess __ID__entification and is a unique
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
          /proc/*/ and returns the process ids of the ones matching the user.
          This is advanced (and also redundant, since lsof does exactly this).

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
