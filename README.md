# R Crash Course 

*Based on [this tutorial](https://www.youtube.com/watch?v=s3FozVfd7q4)*

---


## Content:

### 1.  00:40 Installation

- link to go to to download R : https://cran.r-project.org
- go to R for windows -> click on base -> click Download R 3.6.1 for Windows
- Everything default

### 2.  02:14 R Studio Setup 

- Go to https://www.rstudio.com and download the free version of rstudio
- Install R studio and open it. Console, terminal and jobs appears. You can do everything on a console that you can do in the regular R file
- go to file -> new file -> R script .
- go to file -> save as -> save the file in convenient location
- menu bar -> tools -> global options -> left pane's Appearance -> In Editor Theme choose Tomorrow Night to get dark theme. 
- In console type getwd() to get current directory name
- In menu bar -> session -> Set Working Directory go to the folder you have saved your r's file to set your current working directory there. 

    ```bash

    > getwd()
    [1] "C:/Users/intab/OneDrive/Documents"
    > setwd("F:/python/ml-ai-dl/maths/r_crash")
    > getwd()
    [1] "F:/python/ml-ai-dl/maths/r_crash"

    ```

### 3.  04:12 Fun Example 

- A Scatterplot to see if batting average is directly connected to runs produced.

    ```r
    # Load player data
    mlbPlayers = read.table(file=file.choose(),
                        header=T, sep=" ",
                        na.strings="`",
                        stringsAsFactors=F)

    # Grab just RBIs and Avg for each player
    # playerData is known as a data frame (Table of Data)
    # We get the stats we want by passing that list in a vector
    playerData = mlbPlayers[,c("RBI","AVG")]

    # Create the file
    png(file="player_rbi_avg.png")

    # Create the plot
    plot(x=playerData$RBI, y=playerData$AVG,
        xlab="RBI", ylab="AVG", main="RBIs and Average")

    # Create the file
    dev.off()

    ```
- Select the code and click on run. 
- We haven't specified the path to the data file. When we run the above script a browse window appears in our working directory, where we can specify the data file. After running the script playerrbi_avg.png file is created in the working directory. 

### 4.  09:57 Assignment 

-  You can assign a value using = or <-
    
    ```r

    myNum = 5
    myNum <- 5

    ```

### 5.  10:22 Variables 

- Variable names start with a letter and can contain numbers, underscores and dots

### 6.  10:37 Data Types 

- Most languages use data types to define how much space to set asside in memory, Variables in R are assigned R Objects
- Types are dynamic which means a variable names data type changes based on the data assigned to it
- Here are the Vector types:

    ```r

    # numeric
    print(class(4))

    # integer
    print(class(4L))

    # logical (TRUE, FALSE, T, F)
    print(class(TRUE))

    # complex
    print(class(1 + 4i))

    # character
    print(class("Sample"))

    # raw when converted into raw bytes
    print(class(charToRaw("Sample")))

    ```

- Output in console:

    ```bash

        #numeric
        > print(class(4))
        [1] "numeric"
        > 
        > # integer
        > print(class(4L))
        [1] "integer"
        > 
        > # logical (TRUE, FALSE, T, F)
        > print(class(TRUE))
        [1] "logical"
        > 
        > # complex
        > print(class(1 + 4i))
        [1] "complex"
        > 
        > # character
        > print(class("Sample"))
        [1] "character"
        > 
        > # raw when converted into raw bytes
        > print(class(charToRaw("Sample")))
        [1] "raw"

    ```

- You can check an objects class with is.integer(VAR_NAME), is.numeric(VAR_NAME), is.matrix(VAR_NAME), is.data.frame(VAR_NAME),is.logical(VAR_NAME), is.vector(VAR_NAME), is.character(VAR_NAME)
- You can convert to different classes with as.integer(VAR_NAME), as.numeric(VAR_NAME),...

### 7.  13:33 Arithmetic Operators 

- Usin sprintf we are tyring to print out in console
- Code for addition, subtraction, multiplication, division, modulus and exponent: 

    ```r

    sprintf("4 + 5 = %d", 4 + 5) # %d = integer
    sprintf("4 - 5 = %d", 4 - 5)
    sprintf("4 * 5 = %d", 4 * 5)

    # here we are working with floating values and we have 1 or more value ahead and only 3 after decimal
    sprintf("4 / 5 = %1.3f", 4 / 5) 

    # # Modulus or remainder of division
    sprintf("5 %% 4 = %d", 5 %% 4)
    # 
    # # Value raised to the exponent of the next
    sprintf("4^2 = %d", 4^2) 

    ```

- output in console :

    ```bash

    > sprintf("4 + 5 = %d", 4 + 5) # %d = integer
    [1] "4 + 5 = 9"
    > sprintf("4 - 5 = %d", 4 - 5)
    [1] "4 - 5 = -1"
    > sprintf("4 * 5 = %d", 4 * 5)
    [1] "4 * 5 = 20"
    > 
    > # here we are working with floating values and we have 1 or more value ahead and only 3 after decimal
    > sprintf("4 / 5 = %1.3f", 4 / 5) 
    [1] "4 / 5 = 0.800"
    > 
    > # # Modulus or remainder of division
    > sprintf("5 %% 4 = %d", 5 %% 4)
    [1] "5 % 4 = 1"
    > # 
    > # # Value raised to the exponent of the next
    > sprintf("4^2 = %d", 4^2)
    [1] "4^2 = 16

    ```

### 8.  14:59 Vectors 

- Vectors store multiple values
- Indexing starts at 1

    ```bash

    > # Create a vector
    > numbers = c(3, 2, 0, 1, 8)
    > numbers
    [1] 3 2 0 1 8
    > 
    > # Get value by index
    > numbers[1]
    [1] 3
    > 
    > # Get the number of items
    > length(numbers)
    [1] 5
    > 
    > # Get the last value
    > numbers[length(numbers)]
    [1] 8
    > 
    > # Get everything but an index
    > numbers[-1]
    [1] 2 0 1 8
    > 
    > # Get the 1st 2 values
    > numbers[c(1,2)]
    [1] 3 2
    > 
    > # Get the 2nd and 3rd
    > numbers[2:3]
    [1] 2 0
    > 
    > # Replace a value
    > numbers[5] = 1
    > numbers
    [1] 3 2 0 1 1
    > 
    > # Replace the 4th and 5th with 2
    > numbers[c(4,5)] = 2
    > numbers
    [1] 3 2 0 2 2
    > 
    > # sort values (decreasing can be TRUE or FALSE)
    > # sort(numbers) sorts in increasing direction
    > sort(numbers, decreasing=TRUE)
    [1] 3 2 2 2 0
    > 
    > # Generate a sequence from 1 to 10
    > oneToTen = 1:10
    > oneToTen
    [1]  1  2  3  4  5  6  7  8  9 10
    > 
    > # Sequence from 3 to 27 adding 3 each time
    > add3 = seq(from=3, to=27, by=3)
    > add3
    [1]  3  6  9 12 15 18 21 24 27
    > 
    > # Create 10 evens from 2
    > evens = seq(from=2, by=2, length.out=10)
    > evens
    [1]  2  4  6  8 10 12 14 16 18 20
    > 
    > # Find out if a value is in vector
    > sprintf("4 in evens %s", 4 %in% evens)
    [1] "4 in evens TRUE"
    > 
    > # rep() repeats a value/s x, a number of times and
    > # each defines how many times to repeat each item
    > rep(x=2, times=5, each=2)
    [1] 2 2 2 2 2 2 2 2 2 2
    > 
    > rep(x=c(1,2,3), times=2, each=2)
    [1] 1 1 2 2 3 3 1 1 2 2 3 3
    > 

    ```

### 9.  20:17 Relational Operators

- Consle codes: 

    ```bash

    > iAmTrue = TRUE
    > iAmFalse = FALSE
    > 
    > sprintf("4 == 5 : %s", 4 == 5) # Checking for equality
    [1] "4 == 5 : FALSE"
    > sprintf("4 != 5 : %s", 4 != 5) # not equal to
    [1] "4 != 5 : TRUE"
    > sprintf("4 > 5 : %s", 4 > 5) # gt
    [1] "4 > 5 : FALSE"
    > sprintf("4 < 5 : %s", 4 < 5) # lt
    [1] "4 < 5 : TRUE"
    > sprintf("4 >= 5 : %s", 4 >= 5) # gte
    [1] "4 >= 5 : FALSE"
    > sprintf("4 <= 5 : %s", 4 <= 5) # lte
    [1] "4 <= 5 : TRUE"

    > # Create vector of Trues and Falses depending on condition (is even)
    > isEven = oneTo20 %% 2 == 0 # List with even values 
    > isEven
    [1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE
    [12]  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE
    > 
    > # Create array of evens
    > justEvens = oneTo20[oneTo20 %% 2 == 0]
    > justEvens
    [1]  2  4  6  8 10 12 14 16 18 20

    ```


### 10. 22:15 Logical Operators 

    ```r

    > cat("TRUE && FALSE = ", T && F, "\n")
    TRUE && FALSE =  FALSE 
    > cat("TRUE || FALSE = ", T || F, "\n")
    TRUE || FALSE =  TRUE 
    > cat("!TRUE = ", !T, "\n")
    !TRUE =  FALSE 

    ```

### 11. 23:00 If 

    ```r

    age = 18

    # if, else and else if works like other languages
    if(age >= 18) {
        print("Drive and Vote")
    } else if (age >= 16){
        print("Drive")
    } else {
        print("Wait")
    }

    ```
### 12. 24:04 Switch 

    ```r

    # Used when you have a limited set of possible values
    grade = "Z"

    switch(grade,
        "A" = print("Great"),
        "B" = print("Good"),
        "C" = print("Ok"),
        "D" = print("Bad"),
        "F" = print("Terrible"),
        print("No Such Grade"))

    ```

### 13. 25:34 Strings 

    ```bash
    
    > str1 = "This is a string"
    > 
    > # String length, i.e. the number of characters inside string
    > nchar(str1)
    [1] 16
    

    > # You can compare strings where later letters are considered
    > # greater than the earlier letters
    > sprintf("Dog > Egg : %s", "Dog" > "Egg")
    [1] "Dog > Egg : FALSE"
    > sprintf("Dog == Egg : %s", "Dog" == "Egg")
    [1] "Dog == Egg : FALSE"


    > # Combine strings and define sperator if any
    > str2 = paste("Owl", "Bear", sep="")
    > str2
    [1] "OwlBear"

    > # Remove bear from the string
    > substr(x=str2, start=4, stop=7)
    [1] "Bear"

    > # Substitute one string with another
    > sub(pattern="Owl", replacement="Hawk", x=str2)
    [1] "HawkBear"

    > # Substitute all matches
    > gsub(pattern="Egg", replacement="Chicken", x="Egg Egg")
    [1] "Chicken Chicken"

    > # Split string into vector
    > strVect = strsplit("A dog ran fast", " ")
    > 
    > strVect
    [[1]]
    [1] "A"    "dog"  "ran"  "fast"


    ```

### 14. 29:45 Factors 

- Factors are used when you have a limited number of values that are strings or integers

    ```bash

    > # Create a factor vector
    > direction = c("Up", "Down", "Left", "Right", "Left", "Up")
    > factorDir = factor(direction)
    > # Check if it's a Factor
    > is.factor(factorDir)
    [1] TRUE

    > # Any duplication is not going to appear in the levels which is present in the factor objects. Levels stores all possible values
    > factorDir 
    [1] Up    Down  Left  Right Left  Up   
    Levels: Down Left Right Up

    > levels(x=factorDir)
    [1] "Down"  "Left"  "Right" "Up"

    > # You can define your levels and their orders
    > dow = c("Monday", "Tuesday", "Wednesday", "Thursday",
    +         "Friday", "Saturday", "Sunday")

    > wDays = c("Tuesday", "Thursday", "Monday") #work days schedule

    > # create a factor out of wDays specify levels and orders too
    > wdFact = factor(x=wDays, levels=dow, ordered=T)
    > wdFact
    [1] Tuesday  Thursday Monday  
    7 Levels: Monday < Tuesday < Wednesday < Thursday < ... < Sunday

    ```

### 15. 32:15 Data Frames 

- A Data Frame is a table which contains any type of data and an equal amount of data in each column
- Each row is called a record and each column a varaible

    ```bash



    ```

#### 16. 36:00 Repeat 



### 17. 36:43 While 



### 18. 37:54 For 



### 19. 38:43 Matrices 



### 20. 43:03 Arrays 



### 21. 44:22 Functions 



### 22. 48:44 Anonymous Functions 



### 23. 49:29 Closures 



### 24. 51:30 Exception Handling 



### 25. 53:11 File I/O 



### 26. 58:29 Plotting 



### 27. 1:08:14 Math Functions 



### 28. 1:11:18 Random Numbers



### 29. 1:12:18 Pie Charts 



### 30. 1:17:56 Bar Charts 



### 31. 1:20:12 Regression Analysis


