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
