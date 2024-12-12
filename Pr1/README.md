

# Практическая работа №1

Введение в R

## Цель работы

1.  Разработать отчет с использованием стека технологий Rmarkdown и
    Quarto

2.  Познакомиться с языком R

3.  Пройти обучающие уроки в swirl

## Исходные данные

1.  Ноутбук
2.  ОС Windows
3.  RStudio
4.  R
5.  Github
6.  Swirl

## Общий план выполнения

1.  Установить пакет swirl

2.  Выполнить ознакомительные задания

3.  Оформить отчёт

## Содержание ЛР

### Шаг 1. Установка пакета swirl

**На данном шаге производится установка пакета swirl**

``` r
#install.packages("swirl")
```

### Шаг 2. Выполнение заданий

**На данном шаге происходит выполнение ознакомительных заданий пакет
swirl**

``` r
#swirl::swirl()
```

#### Первое задание (Basic Building Blocks)

``` r
5+7
```

    [1] 12

``` r
x <- 5+7
```

``` r
x
```

    [1] 12

``` r
y <- x - 3
```

``` r
y
```

    [1] 9

``` r
c(1.1, 9, 3.14)
```

    [1] 1.10 9.00 3.14

``` r
z <- c(1.1, 9, 3.14)
```

``` r
?c
```

    starting httpd help server ... done

``` r
z
```

    [1] 1.10 9.00 3.14

``` r
c(z, 555)
```

    [1]   1.10   9.00   3.14 555.00

``` r
c(z, 555, z)
```

    [1]   1.10   9.00   3.14 555.00   1.10   9.00   3.14

``` r
z * 2 + 100
```

    [1] 102.20 118.00 106.28

``` r
my_sqrt <- sqrt(z-1)
```

``` r
1
```

    [1] 1

``` r
my_sqrt
```

    [1] 0.3162278 2.8284271 1.4628739

``` r
my_div <- z / my_sqrt
```

``` r
2
```

    [1] 2

``` r
my_div
```

    [1] 3.478505 3.181981 2.146460

``` r
c(1, 2, 3, 4) + c(0, 10)
```

    [1]  1 12  3 14

``` r
c(1, 2, 3, 4) + c(0, 10, 100)
```

    Warning in c(1, 2, 3, 4) + c(0, 10, 100): longer object length is not a
    multiple of shorter object length

    [1]   1  12 103   4

``` r
z * 2 + 1000
```

    [1] 1002.20 1018.00 1006.28

``` r
my_div
```

    [1] 3.478505 3.181981 2.146460

#### Второе задание Workspace and Files

``` r
getwd()
```

    [1] "C:/Users/ivanu/Универ/ИАТПУИБ/ReportR/Pr1"

``` r
ls()
```

    [1] "my_div"  "my_sqrt" "x"       "y"       "z"      

``` r
x <- 9
```

``` r
ls()
```

    [1] "my_div"  "my_sqrt" "x"       "y"       "z"      

``` r
dir()
```

    [1] "mytest2.R"        "mytest3.R"        "README.qmd"       "README.rmarkdown"
    [5] "testdir"          "testdir2"        

``` r
?list.files
```

``` r
args(list.files)
```

    function (path = ".", pattern = NULL, all.files = FALSE, full.names = FALSE, 
        recursive = FALSE, ignore.case = FALSE, include.dirs = FALSE, 
        no.. = FALSE) 
    NULL

``` r
old.dir <- getwd()
```

``` r
dir.create("testdir")
```

    Warning in dir.create("testdir"): 'testdir' already exists

``` r
setwd("testdir")
```

``` r
file.create("mytest.R")
```

    [1] TRUE

``` r
list.files()
```

    [1] "mytest.R"         "mytest2.R"        "mytest3.R"        "README.qmd"      
    [5] "README.rmarkdown" "testdir"          "testdir2"        

``` r
file.exists("mytest.R")
```

    [1] TRUE

``` r
file.info("mytest.R")
```

             size isdir mode               mtime               ctime
    mytest.R    0 FALSE  666 2024-12-11 22:39:33 2024-12-11 22:39:33
                           atime exe
    mytest.R 2024-12-11 22:39:33  no

``` r
file.rename("mytest.R", "mytest2.R")
```

    [1] TRUE

``` r
file.copy("mytest2.R","mytest3.R")
```

    [1] FALSE

``` r
file.path("mytest3.R")
```

    [1] "mytest3.R"

``` r
file.path("folder1", "folder2")
```

    [1] "folder1/folder2"

``` r
?dir.create
```

``` r
dir.create(file.path('testdir2', 'testdir3'), recursive = TRUE)
```

    Warning in dir.create(file.path("testdir2", "testdir3"), recursive = TRUE):
    'testdir2\testdir3' already exists

``` r
setwd(old.dir)
```

#### Третье задание Sequences of Numbers

``` r
1:20
```

     [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20

``` r
pi:10
```

    [1] 3.141593 4.141593 5.141593 6.141593 7.141593 8.141593 9.141593

``` r
15:1
```

     [1] 15 14 13 12 11 10  9  8  7  6  5  4  3  2  1

``` r
?":"
```

``` r
seq(1, 20)
```

     [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20

``` r
seq(0, 10, by=0.5)
```

     [1]  0.0  0.5  1.0  1.5  2.0  2.5  3.0  3.5  4.0  4.5  5.0  5.5  6.0  6.5  7.0
    [16]  7.5  8.0  8.5  9.0  9.5 10.0

``` r
my_seq <- seq(5, 10, length=30)
```

``` r
length(my_seq)
```

    [1] 30

``` r
1:length(my_seq)
```

     [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
    [26] 26 27 28 29 30

``` r
seq(along.with = my_seq)
```

     [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
    [26] 26 27 28 29 30

``` r
seq_along(my_seq)
```

     [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
    [26] 26 27 28 29 30

``` r
rep(0, times = 40)
```

     [1] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
    [39] 0 0

``` r
rep(c(0, 1, 2), times = 10)
```

     [1] 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2

``` r
rep(c(0, 1, 2), each = 10)
```

     [1] 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2

#### Четвертое задание Vectors

``` r
num_vect <- c(0.5, 55, -10, 6)
```

``` r
tf <- num_vect < 1
```

``` r
2
```

    [1] 2

``` r
tf
```

    [1]  TRUE FALSE  TRUE FALSE

``` r
num_vect >= 6
```

    [1] FALSE  TRUE FALSE  TRUE

``` r
2
```

    [1] 2

``` r
1
```

    [1] 1

``` r
1
```

    [1] 1

``` r
my_char <- c("My", "name", "is")
```

``` r
my_char
```

    [1] "My"   "name" "is"  

``` r
paste(my_char, collapse = " ")
```

    [1] "My name is"

``` r
my_name <- c(my_char, "Artem")
```

``` r
my_name
```

    [1] "My"    "name"  "is"    "Artem"

``` r
paste(my_name, collapse = " ")
```

    [1] "My name is Artem"

``` r
paste("Hello", "world!", sep = " ")
```

    [1] "Hello world!"

``` r
paste(1:3,c("X", "Y", "Z"),sep = "")
```

    [1] "1X" "2Y" "3Z"

``` r
paste(LETTERS, 1:4, sep = "-")
```

     [1] "A-1" "B-2" "C-3" "D-4" "E-1" "F-2" "G-3" "H-4" "I-1" "J-2" "K-3" "L-4"
    [13] "M-1" "N-2" "O-3" "P-4" "Q-1" "R-2" "S-3" "T-4" "U-1" "V-2" "W-3" "X-4"
    [25] "Y-1" "Z-2"

#### Пятое задание Missing Value

``` r
x <- c(44, NA, 5, NA)
```

``` r
x * 3
```

    [1] 132  NA  15  NA

``` r
y <- rnorm(1000)
```

``` r
z <- rep(NA, 1000)
```

``` r
my_data <- sample(c(y, z), 100)
```

``` r
my_na <- is.na(my_data)
```

``` r
my_na
```

      [1]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE FALSE  TRUE FALSE FALSE  TRUE FALSE
     [13] FALSE  TRUE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE FALSE  TRUE  TRUE
     [25] FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE FALSE
     [37]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE FALSE FALSE  TRUE  TRUE FALSE
     [49]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE FALSE
     [61] FALSE FALSE FALSE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE FALSE FALSE  TRUE
     [73] FALSE FALSE  TRUE FALSE  TRUE  TRUE FALSE FALSE  TRUE  TRUE  TRUE  TRUE
     [85]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE
     [97] FALSE FALSE FALSE FALSE

``` r
my_data == NA
```

      [1] NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA
     [26] NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA
     [51] NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA
     [76] NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA

``` r
sum(my_na)
```

    [1] 57

``` r
my_data
```

      [1]          NA          NA -1.51088565          NA          NA          NA
      [7] -0.43542628          NA -1.91714030  0.17302129          NA  0.87684796
     [13]  0.78984922          NA -0.06208367          NA          NA          NA
     [19] -0.37202926          NA          NA  0.67736743          NA          NA
     [25] -1.66370029          NA          NA -0.57648163  1.31546455  0.39977013
     [31] -0.28932144          NA  2.63576429          NA -2.08579833 -1.12503301
     [37]          NA          NA          NA -1.15154875          NA          NA
     [43]          NA  0.35424042  1.70119460          NA          NA -0.13713860
     [49]          NA          NA -0.87817271          NA          NA          NA
     [55]          NA          NA          NA  0.53462796          NA -0.06279325
     [61]  0.08148367 -0.86515081 -0.35521984          NA          NA -1.14678561
     [67]          NA          NA          NA  0.26814382  0.13835661          NA
     [73]  1.95304704  0.96656848          NA  0.44813446          NA          NA
     [79] -0.13250448  0.40076246          NA          NA          NA          NA
     [85]          NA -0.91068865          NA          NA          NA          NA
     [91]          NA -1.29657550 -0.79825622 -1.11641096          NA          NA
     [97]  1.35070550 -2.29443019 -0.95823527  1.89449212

``` r
0 / 0
```

    [1] NaN

``` r
Inf - Inf
```

    [1] NaN

## Оценка результатов

Произведена работа с языком R, знакомство с основами данного языка с
использованием заданий swirl

## Вывод

По итогу данной работы были изучены основы языка R с помощью учебных
заданий swirl
