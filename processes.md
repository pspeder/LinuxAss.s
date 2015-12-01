#Processes, Opened files and user sessions
This file intends to introduce some of the most common tools available when
working with Linux system administration.
An incomplete list of the applications you will/should use to solve these assignments:
* `who`
* `ps`
* `lsof`

...some of these (namely, `ps` and `lsof`) are __beasts__ of commands - they both
have a vast list of command line switches (see
[general linux file](./general-linux.md)), and a plethora of use
cases, thus, being able to search in `man` pages is of importance (you do that by
typing `/` then your search term, and then press `<ENTER>`, when reading the
`man`-page).

You are advised to read the man page of all commands that are named here.
Specifically, I would recommend reading the "options" and/or "switches" section(s)
of said `man`-pages, as these are key to understanding the operation of such
programmes.

###Purpose
The purpose of these exercise is yo allow you to find out a solution on your own.
The exercises does not specify which programmes you should use, rather, you are
encouraged to solve them with as many different tools as possible. This will
hopefully give you some intuition of which tool is right for the job in the
future.


#Assignments
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

