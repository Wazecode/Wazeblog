---
categories: notes rlang
---
- [1. What is R? and Data Types.](#1-what-is-r-and-data-types)
  - [1.a Download, Install, Configure](#1a-download-install-configure)
    - [Install R](#install-r)
    - [Install Rstudio](#install-rstudio)
  - [1.b Learn to use help() function](#1b-learn-to-use-help-function)
    - [Example](#example)
    - [Output:](#output)
  - [1.c Understanding DataTypes in R](#1c-understanding-datatypes-in-r)
    - [Example:](#example-1)
    - [Output:](#output-1)
  - [1.d Covert Data types in R](#1d-covert-data-types-in-r)
    - [Example Code:](#example-code)
    - [Output:](#output-2)
- [2. Getting Data in and Out of R](#2-getting-data-in-and-out-of-r)
  - [2.a.1 Create (Vectors, Matrix, Dataframe)](#2a1-create-vectors-matrix-dataframe)
    - [Vectors](#vectors)
    - [Matrix](#matrix)
    - [Dataframe](#dataframe)
    - [Matrix vs DataFrame](#matrix-vs-dataframe)
  - [2.a.2 Finding (Vectors, Matrix, Dataframe)](#2a2-finding-vectors-matrix-dataframe)
    - [which()](#which)
      - [Example with Vectors](#example-with-vectors)
      - [Example with Dataframes](#example-with-dataframes)
    - [A Program to print the row whose marks in 45](#a-program-to-print-the-row-whose-marks-in-45)
    - [Match()](#match)






# 1. What is R? and Data Types.
## 1.a Download, Install, Configure
### Install R
- Go to [CRAN R project](https://cran.r-project.org/) website.
- Click on the Download R for Windows link.
- Click on the base subdirectory link or install R for the first time link.
- Click Download R X.X.X for Windows (X.X.X stand for the latest version of R. eg: 3.6.1) and save the executable .exe file.
- Install the .exe file.

### Install Rstudio
- With R-base installed, let’s move on to installing RStudio. To begin, go to [download RStudio](http://www.rstudio.com/ide/download) and click on the download button for RStudio desktop.
- Click on the link for the windows version of RStudio and save the .exe file.
- Install the .exe file.

## 1.b Learn to use help() function
The help() function in R is used to get help on any given R function passed to it.

```r
help(function name)
```
- **Parameter value** : The help() function takes the parameter value function name which represents the name of any R function.
- **Return value** : The help() function returns access to official documentation pages of the function passed to it.

### Example
We are going to get help for eval function in R.

```r
help(eval)
```

### Output:

```r
eval                   package:base                    R Documentation

Evaluate an (Unevaluated) Expression

Description:

     Evaluate an R expression in a specified environment.

Usage:

     eval(expr, envir = parent.frame(),
                enclos = if(is.list(envir) || is.pairlist(envir))
                            parent.frame() else baseenv())
     evalq(expr, envir, enclos)
     eval.parent(expr, n = 1)
     local(expr, envir = new.env())
     
Arguments:

    expr: an object to be evaluated.  See ‘Details’.

   envir: the ‘environment’ in which ‘expr’ is to be evaluated.  May
          also be ‘NULL’, a list, a data frame, a pairlist or an
          integer as specified to ‘sys.call’.

  enclos: Relevant when ‘envir’ is a (pair)list or a data frame.
          Specifies the enclosure, i.e., where R looks for objects not
          found in ‘envir’.  This can be ‘NULL’ (interpreted as the
          base package environment, ‘baseenv()’) or an environment.

       n: number of parent generations to go back

Details:

     ‘eval’ evaluates the ‘expr’ argument in the environment specified
     by ‘envir’ and returns the computed value.  If ‘envir’ is not
     specified, then the default is ‘parent.frame()’ (the environment
     where the call to ‘eval’ was made).
...
```

## 1.c Understanding DataTypes in R
- Basic data types in R can be divided into the following types:
1. numeric - (10.5, 55, 787)
2. integer - (1L, 55L, 100L, where the letter "L" declares this as an integer)
3. complex - (9 + 3i, where "i" is the imaginary part)
4. character (a.k.a. string) - ("k", "R is exciting", "FALSE", "11.5")
5. logical (a.k.a. boolean) - (TRUE or FALSE)
6. A raw data type specifies values as raw bytes.
  
### Example:

```r
# datatypes
a = 5
print(typeof(a))

i = 7L
print(typeof(i))

c = 3 + 8i
print(typeof(c))

k = "k"
print(typeof(k))

b = TRUE
print(typeof(b))

x = as.raw(0x32)
print(x)

```

### Output:

```r
[1] "double"
[1] "integer"
[1] "complex"
[1] "character"
[1] "logical"
[1] 32
```

## 1.d Covert Data types in R
### Example Code:

```r
x = 10
print(typeof(x))
X = as.character(x)
print(typeof(X))

y = "77"
print(typeof(y))
Y = as.numeric(y)
print(typeof(Y))
```

### Output:

```r
[1] "double"
[1] "character"
[1] "character"
[1] "double"
```


# 2. Getting Data in and Out of R

## 2.a.1 Create (Vectors, Matrix, Dataframe)

### Vectors

```r
v1 = c('a', 'b', 'c', 'd')
v2 = c(1, 2 , 3, 4)

cbind(v1, v2)

Output: 
     v1  v2 
[1,] "a" "1"
[2,] "b" "2"
[3,] "c" "3"
[4,] "d" "4"

```

### Matrix
```r
mat = matrix(c(1:6), nrow = 2)
mat

Output: 

     [,1] [,2] [,3]
[1,]    1    3    5
[2,]    2    4    6

as.vector(mat)

Output: 

[1] 1 2 3 4 5 6
```

### Dataframe
```r
> data.frame(v1,v2)
  v1 v2
1  a  1
2  b  2
3  c  3
4  d  4

> as.data.frame(mat)
  V1 V2 V3
1  1  3  5
2  2  4  6

> bca = data.frame(
+   roll = c(1:6),
+   name = c('Sai', 'Ram', 'Sid', 'Raj', 'Jamal', 'Simi'),
+   marks = c(50, 78, 45, 91, 89, 99)
+ )

> bca
  roll  name marks
1    1   Sai    50
2    2   Ram    78
3    3   Sid    45
4    4   Raj    91
5    5 Jamal    89
6    6  Simi    99

> as.matrix(bca)
     roll name    marks
[1,] "1"  "Sai"   "50" 
[2,] "2"  "Ram"   "78" 
[3,] "3"  "Sid"   "45" 
[4,] "4"  "Raj"   "91" 
[5,] "5"  "Jamal" "89" 
[6,] "6"  "Simi"  "99" 

```

### Matrix vs DataFrame

The main difference is that matrices can only contain a single class of data, while data frames can consist of many different classes of data.


## 2.a.2 Finding (Vectors, Matrix, Dataframe)
### which() 

- The which function in R returns the position of the values in the logical vector.
```r
which(x,arr.ind = F,useNames = F)
```
Where,
\newline
- X = An input logical vector. \newline
- Arr.ind = Returns the array indices if x is an array.  \newline
- useNames = Indicates the dimension names of an array. 

#### Example with Vectors

```r
> vec1 = c(0, 23, 45, 87, 101, 130, 157, 87, 23, 101, 87)
> 
> which(vec1 == 87)
[1]  4  8 11
> 
> which(vec1 == 44)
integer(0)
> which(vec1 == 0)
[1] 1
```


#### Example with Dataframes

```r
> bca 
  roll  name marks
1    1   Sai    50
2    2   Ram    78
3    3   Sid    45
4    4   Raj    91
5    5 Jamal    89
6    6  Simi    99
>
> which(bca$marks == 50)
[1] 1
>
> which(bca$marks > 50)
[1] 2 4 5 6
>
> which(bca$name == "Raj")
[1] 4
```

### A Program to print the row whose marks in 45

```r
> bca[which(bca$marks == 45), ]
  roll name marks
3    3  Sid    45

```


### Match()
- The match() function in R returns the position of the first match between two objects.

This function uses the following basic syntax:

```r
match(object1, object2)
```

Example:

```r
> vec1
 [1]   0  23  45  87 101 130 157  87  23 101  87
> 
> match(87, vec1)
[1] 4
> match(c(87,101), vec1)
[1] 4 5
> 
> 
> bca
  roll  name marks
1    1   Sai    50
2    2   Ram    78
3    3   Sid    45
4    4   Raj    91
5    5 Jamal    89
6    6  Simi    99
> match(45,bca$marks)
[1] 3
```

