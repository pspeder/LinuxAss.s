#The programmes: sed and awk
[`sed`]() and [`awk`]() are both
[turing complete](http://www.catonmat.net/blog/proof-that-sed-is-turing-complete/)
programming languages that are installed on most linux systems.

They are mainly used to filter text, and do that in different ways. One might
think of them as a regex-engine, to extract and filter output data from some
other program. For instance:

    lsb_release -i | awk '\''{ print $NF }'\'

...which will display which distribution of linux you are using (if the
mentioned programmes are installed, that is).
