#Shell Pimpin'
So, now that you're somewhat more confident in a terminal, let's shake up
the shell a little.

Please note that this is pretty much a `bash`-oriented guide, also this is
one the areas in which zsh sets itself apart - it is somewhat more customizable
one might say: I realise it not be a totally fair comparison, but `man bash`
is ~7250 lines, against `man zshall`'s ~33500, which may not be a totally skewed
picture... just saying :).

##How and when the shell loads what files
So you may have noticed those files in your home drive, all relating to
`bash` somehow. Those determine, what your terminal looks and feels like
(what language applications should choose, preferred editor or browser,
what information the "prompt" should show), also what programmes you are
able to run and where programmes should look to find certain files they
might need.

The files are loaded in a specific order, which I think is explained well
[here](https://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html)
and [here](https://shreevatsa.wordpress.com/2008/03/30/zshbash-startup-files-loading-order-bashrc-zshrc-etc/)

N.B. If you did not read the above: beware, not all files are loaded for all
shells environments you will meet.

##Da Pimpin'
1. Make a shell that looks like this:
  ```
  ehlm@hamstarch l:118 > █
  ```
  ...where:
  * ehlm is coloured with your terminals green colour
  * hamstarch is coloured with a colour of your own choosing
  * `l` stands for line and corresponds to which line in your terminal
    that you are currently about to enter.

  Recommended reading:
  * http://ss64.com/bash/syntax-prompt.html : a brief overview of shell customisation

2. Take a piece of paper and describe (with words and/or illustration) how
  you would like your prompt to look.

  Specifically, you should consider some of the following:
  * which information do you want displayed,
  * should it be a minimalistic terminal or would you prefer to have, for
    instance, version control information displayed when you're in a repos,
  * maybe you want a 2-liner prompt, with room for displaying all sorts of
    things, including: mail count, battery level, network signal, date/time,

  Recommended reading:
  * http://www.caliban.org/bash/index.shtml : some (a few) sensible defaults

3. Take a look at the available options in bash, and try changing some with
  a command like:
  ```
  set -o dotglob # allow files beginning with '.' to be returned in the
                 # results of path-name expansion (autocompletion e.g.)
  ```
  ...remember that these setting will only apply to shell that you have typed
  the command, to make it permanent, add it to your `~/.bashrc`-file.

5. Search the web for others' configs. Quite a lot of useful hacks out there.

6. Implement the prompt you designed in step 2.
