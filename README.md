# LinuxAss.s
Various assignments to get linux administration as well as shell scripting under the skin.

#CLI-tools
CLI stands for Command Line Interface. The contents of this folder
is exercises (and perhaps a few notes and hints) for some common applications
that run inside a terminal (or terminal emulator), relating to administration
of a Linux system.

Most (if not all) of the applications described in this folder are available on
all modern linux distros (Ubuntu and Archlinux included), and will often be
installed as part of the base system. Use your package manager to install them
if the commands do not exist.

#Scripting
Some of the exercises will tell you to write down the answer as a script.
I encourage you to do so whenever you see a command you might want to use
in the future, regardless of stated or not.

##Local `bin`-dir (binary/script directory)
If you want to, you may create a folder in your home directory, which can
be used for storing scripts, and also allow you to execute those scripts
from anywhere, just as you would any other installed program.

    # First create the directory
    mkdir ~/bin
    # Then append that folder to your "environment variable" $PATH
    export PATH="$PATH:~/bin"
    # To make the change permanent, add the line above to your shell's
    # configuration file (here for the bash shell)
    echo 'export PATH="$PATH:~/bin"' >> ~/.bashrc

Then you just need to save your scripts there and make them executable,
as in the example below:

    # 1. Create the script
    echo '#!/bin/bash\necho "\tU wot m8?"' > ~/bin/britishslang.sh
    # 2. Make the script executable (for the file owner (should be your user))
    sudo chmod u+x ~/bin/britishslang.sh

    # Now you may run it from anywhere
    cd /
    britishslang.sh
            U wot m8!?

#Reading order
I have created subfolders for the programmes I would like to train you in,
but many of them yet remain empty.

Start out by reading about [general linux](general-linux.md), as this will
hopefully aid you in reading the rest of the articles.<br/>
Then move on to [processes](processes.md) for the first set of assignments.
