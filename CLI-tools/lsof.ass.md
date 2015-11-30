1. Få vist alle filer, der er åbnet af din bruger -- også dem du ikke manuelt
   har åbnet selv. Skriv dem gerne til en fil.
  * HINT: `lsof`

  * Solution1:

    lsof -u ehlm

  * Solution2:

    lsof -u ehlm > ~/outputfile.txt

2. Tæl antallet af linjer i outputtet fra 1. vha. commandline
  * HINT1: `wc` står for 'word count' - ikke 'water closet' i din shell
  * HINT2: `wc --help`

  * Solution1:

    lsof -u ehlm | wc -l

  * Solution2:

    #Can probably be simplified:
    lsof -u ehlm > ~/outputfile.txt && wc -l ~/outputfile.txt

3. Lav et script der gør 1., men som ikke skriver noget til stdout
   HINT: søgetermen "stdout redirection" vil finde de relevante resourcer

  * Solution1:

    #!/bin/bash
    # Redirect all output (both std[out|error]) to /dev/null
    lsof -u ehlm 2&> /dev/null


<!--- vim: ft=markdown foldmethod=marker
--->
