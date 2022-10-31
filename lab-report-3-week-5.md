# Researching Commands


## Command - less

### Option 1: `less -N (Filename)`

Example 1
```
$ less -N technical/biomed/1468-6708-3-1.txt

      1
      2
      3
      4
      5         Introduction
      6         Older adults are frequently counseled to lose weight,
      7         even though there is little evidence that overweight is
      8         associated with increased mortality in those over age 65.
      9         Six large controlled population-based studies of
     10         non-smoking older adults have investigated the association
     11         between body mass index (BMI) and mortality, controlling
     12         for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
     13         excess risk for persons with very low BMI, but that persons
     14         with moderately high BMI had little or no extra risk except
     15         in certain small subsets. A review of 13 studies of older
     16         adults drew similar conclusions [ 7 ] .
```
Example 2
```
$ less -N technical/biomed/1472-6769-1-2.txt

    103         1, as the uniform global minimum for
    104         both gas phase and solution models (Table 3). The next
    105         lowest conformer is predicted to be 15-25 kcal/mol higher
    106         in energy, while overall conformer ranking between the
    107         different force fields generally inharmonious. Thus,
    108         incorporation of ESP charges amplifies and alters the
    109         energy rankings. 5) AM1 and PM3 calculations in the gas
    110         phase vary in suggesting
    111         2 ,
    112         6 and
    113         7 as most stable (Table 4). While H
    114         2 O solvation correctly identifies polar
```
Example 3
```
$ less -N technical/911report/chapter-1.txt

      4 "WE HAVE SOME PLANES"
      5
      6     Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern Uni      6 ted States. Millions of men and women readied themselves for work. Some made their way to      6  the Twin Towers, the signature structures of the World Trade Center complex in New York 
      6 City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the 
      6 United States Congress was back in session. At the other end of Pennsylvania Avenue, peop      6 le began to line up for a White House tour. In Sarasota, Florida, President George W. Bus      6 h went for an early morning run.
```
* While seemingly simple at first, less -N could be used as an easier way to identify a specific desired line, as it labels each line with a number. This way if output were saved to a document it could then be accessed by code easier by just asking for a specific line number. An interesting issue I uncovered while using Less -N on the third example was that multiple lines were labelled as 6 instead of ...7,8,9, etc, as shown in the example. Additionally, when I initially copy-pasted this example, it seems there isn't any line return between each line labelled 6, instead it registered as a single unbroken line when I pasted it.

### Option 2: `less +F (Filename)`
Example 1
```
less +F technical/biomed/1468-6708-3-1.txt

        Abbreviations
        BMI Body mass index
        CESD Center for Epidemiologic Studies Depression
        Scale
        CHS Cardiovascular Health Study
        EVGFP Is your health excellent, very good, good, fair or
        poor?
        QALY Quality-adjusted life years
        YHL Years of healthy life
        YOL Years of life



Waiting for data... (interrupt to abort)
```
Example 2 (With the `less +F` command still running, I editied the actual .txt file by adding "This is a Test" after the last line displayed here.)
```
        Abbreviations
        BMI Body mass index
        CESD Center for Epidemiologic Studies Depression
        Scale
        CHS Cardiovascular Health Study
        EVGFP Is your health excellent, very good, good, fair or
        poor?
        QALY Quality-adjusted life years
        YHL Years of healthy life
        YOL Years of life



Test



Waiting for data... (interrupt to abort)
```
Example 3 (`less +F` is still running, and this time I typed "123 \n Testing Testing 123 \n ...18 spaces... This is testing where it detects input")
```
        Abbreviations
        BMI Body mass index
        CESD Center for Epidemiologic Studies Depression
        Scale
        CHS Cardiovascular Health Study
        EVGFP Is your health excellent, very good, good, fair or
        poor?
        QALY Quality-adjusted life years
        YHL Years of healthy life
        YOL Years of life



Test






sting 123



This is testing where it detects input



Waiting for data... (interrupt to abort)
```
* From the article by Linuxize.com I found `less +F` on, "the `+f` option tells `less` to watch the file contents for changes. This is useful when opening log files." From my limited understanding, this command therefore could allow a user to see info on a program as it runs if a log file was regularly updated with it's progress. The reason my inputs were cut off until I tabbed forward 18 spaces is likely because log files seem to be printed in a format that has at the current time at the start of a new line, so `less +F` is likely made to ignore that information stored at the front.

### Option 3: `less -X (Filename)`
Example 1
```
less -X technical/biomed/1468-6708-3-1.txt

        Introduction
        Older adults are frequently counseled to lose weight,     
        even though there is little evidence that overweight is   
        associated with increased mortality in those over age 65. 
        Six large controlled population-based studies of
        non-smoking older adults have investigated the association
        between body mass index (BMI) and mortality, controlling  
        for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
        excess risk for persons with very low BMI, but that persons
        with moderately high BMI had little or no extra risk except
        in certain small subsets. A review of 13 studies of older
:
```
Example 2 (pressed q)
```
$ less -X technical/biomed/1468-6708-3-1.txt

  
    
      
        Introduction
        Older adults are frequently counseled to lose weight,     
        even though there is little evidence that overweight is   
        associated with increased mortality in those over age 65. 
        Six large controlled population-based studies of
        non-smoking older adults have investigated the association
        between body mass index (BMI) and mortality, controlling  
        for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
        excess risk for persons with very low BMI, but that persons
        with moderately high BMI had little or no extra risk except
        in certain small subsets. A review of 13 studies of older

TheWi@DESKTOP-TJUDNTT MINGW64 ~/Documents/GitHub/docsearch (main)
$
```
Example 3 (Entered into a different file and exited.)
```
$ less -X technical/biomed/1468-6708-3-1.txt




        Introduction
        Older adults are frequently counseled to lose weight,
        even though there is little evidence that overweight is
        associated with increased mortality in those over age 65.
        Six large controlled population-based studies of
        non-smoking older adults have investigated the association
        between body mass index (BMI) and mortality, controlling
        for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
        excess risk for persons with very low BMI, but that persons

TheWi@DESKTOP-TJUDNTT MINGW64 ~/Documents/GitHub/docsearch (main)
$ less -X technical/911report/chapter-10.txt



            WARTIME
            After the attacks had occurred, while crisis managers were still sorting out a number                of unnerving false alarms, Air Force One flew to Barksdale Air Force Base in     
                Louisiana. One of these alarms was of a reported threat against Air Force One    
                itself, a threat eventually run down to a misunderstood communication in the hectic
                White House Situation Room that morning.

            While the plan at the elementary school had been to return to Washington, by the time                Air Force One was airborne at 9:55 A.M. the Secret Service, the President's      

TheWi@DESKTOP-TJUDNTT MINGW64 ~/Documents/GitHub/docsearch (main)
$
```
* While not as useful as the last, `less -X` could be a helpful tool in checking multiple files by having a bash script go to certain points in files and exiting, leaving the important parts of the files the user wanted to check on the terminal for them to look at.