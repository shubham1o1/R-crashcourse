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
- So we haven't specified the path to the data file. When we run the above script a browse window appears in our working directory, where we can specify the data file. After running the script playerrbi_avg.png file is created in the working directory. 

### 4.  09:57 Assignment 

-  You can assign a value using = or <-
    
    ```r

    myNum = 5
    myNum <- 5

    ```

#### 5.  10:22 Variables 

- 

#### 6.  10:37 Data Types 
#### 7.  13:33 Arithmetic Operators 
#### 8.  14:59 Vectors 
#### 9.  20:17 Relational Operators 
#### 10. 22:15 Logical Operators 
#### 11. 23:00 If 
#### 12. 24:04 Switch 
#### 13. 25:34 Strings 
#### 14. 29:45 Factors 
#### 15. 32:15 Data Frames 
#### 16. 36:00 Repeat 
#### 17. 36:43 While 
#### 18. 37:54 For 
#### 19. 38:43 Matrices 
#### 20. 43:03 Arrays 
#### 21. 44:22 Functions 
#### 22. 48:44 Anonymous Functions 
#### 23. 49:29 Closures 
#### 24. 51:30 Exception Handling 
#### 25. 53:11 File I/O 
#### 26. 58:29 Plotting 
#### 27. 1:08:14 Math Functions 
#### 28. 1:11:18 Random Numbers 
#### 29. 1:12:18 Pie Charts 
#### 30. 1:17:56 Bar Charts 
#### 31. 1:20:12 Regression Analysis