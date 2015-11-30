#Solutions to exercises in usage of the `lsof` command

* Exercise 1:
  1. Solution without writing to file

    lsof -u ehlm

  2. Redirection of output to a file

    lsof -u ehlm > ~/output.txt

* Exercise 2:
  1. Pipe output to the next command

    lsof -u ehlm | wc -l

  2. There might be a better way to do this:

    [[ lsof -u ehlm > ~/output.txt ]] &&wc -l ~/output.txt

* Exercise 3:
  1. Redirect stdout to /dev/null

```
#!/bin/bash
# This script will redirect all output to /dev/null, in order to suppress output

# This line will redirect all output, but return the exit status code of lsof (your terminal might show this)
lsof -u ehlm &> /dev/null

# This line will redirect all output, and additionally suppress the exit code (this might come in useful when scripting)
#lsof -u ehlm |&> /dev/null
```

