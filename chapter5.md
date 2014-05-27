--- 
title_meta  : Chapter 5
title       : Data frames
description : Most datasets you'll be working with will be stored as a data frame. By the end of this chapter, you'll be able to create a data frame, select interesting parts of a data frame and order a data frame according to certain variables. 
framework   : datacamp
mode        : selfcontained

---

## What's a data frame?

You may remember from the chapter about matrices that all the elements you put in a matrix should be of the same type. Back then, your dataset on Star Wars only contained numeric elements. 

However, when doing a market research survey you often have questions such as:
- 'Are your married?' or a 'yes/no' questions (= boolean data type)
- 'How old are you?' (= numeric data type)
- 'What is your opinion on this product?' or other 'open- ended' questions(= character data type)
- ...

The output when doing the above survey on a number of respondents, is a dataset of different data types. You will often find yourself working with datasets containing different data types instead of only one. 

A data frame has the variables of a dataset as columns and the observations as rows. This will be a familiar concept for those coming from different statistical software packages such as SAS or SPSS.

*** =instructions
	- Click Submit Answer. The data from the built-in example data frame `mtcars` will be printed to the console.

*** =hint
Just click Submit Answer!

*** =sample_code


```r
mtcars  # Built-in R dataset stored in a data frame
```


*** =solution


```r
# Just click the Run button
```


*** =sct


```r
if (!(isTRUE(try(output_contains("mtcars")))){
	DM.result = list(FALSE, "Make sure you output 'mtcars'.");
} else {
	DM.result = list(TRUE, "Great! Continue to the next exercise.");
}
```


*** =pre_exercise_code




---

## Quick, have a look at your dataset

Wow, that's a lot of cars! 

Working with large datasets is not uncommon in data analysis. When working with (extremely) large datasets and data frames, your first task as a data analyst is to develop a clear understanding of its structure and main elements. Therefore, it is often useful to show only a small part of the entire dataset. 

So how to do this in R?
- The function `head()` enables you to show the first observations of a data frame (or any R object you pass to it).
- Unoriginally, the function `tail()` prints out the last observations in your dataset.

Both `head()` and `tail()` also print a top line called the 'header', which contains the names of the different variables in your dataset.

*** =instructions
	- Give an overview of the `mtcars` data set by printing its first observations and the corresponding header.

*** =hint
Use the `head()` function and ask the head of `mtcars`.

*** =sample_code


```r
# Have a quick look at your data
```


*** =solution


```r
head(mtcars)
```


*** =sct


```r
if (!(isTRUE(try(output_contains("head(mtcars)")))){
	DM.result = list(FALSE, "Make sure you use the 'head()' function on 'mtcars'.");
} else {
	DM.result = list(TRUE, "Great! Continue to the next exercise.");
}
```


*** =pre_exercise_code




---

## Have a look at the structure

Another, often used, method to get a rapid overview of your data is the function `str()`. The function `str()` shows you the structure of your dataset. For a data frame it tells you:

- The total number of observations (e.g. 32 car types)
- The total number of variables (e.g. 11 car features)
- A full list of the variables names (e.g. mpg, cyl ... )
- The data type of each variable (e.g. num for car features)
- The first observations

Applying the `str()` function will often be the first thing you do when receiving a new dataset or data frame. It is a great way to get more insight in your dataset before diving into the real analysis!

*** =instructions
	- Investigate the structure of the `mtcars`. Make sure you see the same numbers, variables and data types as  mentioned above.

*** =hint
Use the `str()` function with `mtcars` as input!

*** =sample_code


```r
# Investigate the structure of the mtcars dataset to get started!
```


*** =solution


```r
# Investigate the structure of the mtcars dataset to get started!
str(mtcars)
```


*** =sct


```r
if (!(isTRUE(try(output_contains("str(mtcars)")))){
	DM.result = list(FALSE, "Make sure you use the 'str()' function on 'mtcars'.");
} else {
	DM.result = list(TRUE, "Great! Continue to the next exercise.");
}
```


*** =pre_exercise_code





---

## Creating a data frame 

Since using built-in datasets is not even half the fun of creating your own datasets, the rest of this chapter is based on your personally developed dataset. So put your jet pack on, because it is time for some good old fashioned space exploration! 

As a first goal, you want to construct a data frame that describes the main characteristics of 8 planets in our solar system. According to your good friend Buzz the main features of a planet are:
- The type of planet (Terrestrial or Gass Giant).
- The planet's diameter relative to the diameter of the earth.
- The planet's rotation across the sun relative to that of earth.
- If the planet has rings or not (TRUE or FALSE).

After doing some high-quality research on [wikipedia](http://en.wikipedia.org/wiki/Planet), you feel confident enough to create the necessary vectors: planets, type, diameter, rotation and rings (see editor, note that an element of one vector is linked to the element of another vector based on its position).

You construct a data frame with the `data.frame` function. As arguments, you should provide the above mentioned vectors as input that should become the different columns of that data frame. Therefore, it is important that each vector used to construct a data frame has an equal length. But do not forget, it is possible (and likely) they have different types of data.

*** =instructions
	- Use the function `data.frame` to construct a data frame. Call this variable `planets_df`.

*** =hint
The `data.frame(col1,col2,col3,...)` function takes as arguments the vectors that will become the columns of the data frame. The columns in this case are (in this order): planet, type, diameter, rotation and rings.

*** =sample_code


```r
planets = c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", 
    "Neptune")
type = c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
    "Gass giant", "Gass giant", "Gass giant", "Gass giant")
diameter = c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation = c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings = c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

# Create the data frame:
```


*** =solution


```r
planets = c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", 
    "Neptune")
type = c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
    "Gass giant", "Gass giant", "Gass giant", "Gass giant")
diameter = c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation = c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings = c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

planets_df = data.frame(planets, type, diameter, rotation, rings)

str(planets_df)
```


*** =sct


```r
if (!exists("planets_df")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'planets_df'.")
} else if (!isTRUE(try(all.equal(planets_df, data.frame(planets, type, diameter, 
    rotation, rings))))) {
    DM.result = list(FALSE, "Make sure to assign the correct order of arguments to the data.frame 'planets_df'. The correct order is planets, type, diameter, rotation and rings.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code




---

## Creating a data frame (2)

Make sure you have 8 observations and 5 variables. (The `planets_df` has been loaded in the workspace.)

*** =instructions
	- Use of the function `str()` to investigate the structure of the new `planets_df` variable.

*** =hint
This is easy, no hints ;-)!

*** =sample_code


```r
# Check the structure of planets_df
```


*** =solution


```r
# Check the structure of planet.df
str(planets_df)
```


*** =sct


```r
if (!(isTRUE(try(output_contains("str(planets_df)")))){
	DM.result = list(FALSE, "Make sure you use the 'str()' function on 'planets_df'.");
} else {
	DM.result = list(TRUE, "Great! Continue to the next exercise.");
}
```


*** =pre_exercise_code


```r
planets = c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", 
    "Neptune")
type = c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
    "Gass giant", "Gass giant", "Gass giant", "Gass giant")
diameter = c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation = c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings = c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

planets_df = data.frame(type, planets, diameter, rotation, rings)
```



---

## Selection of data frame elements

Similar to vectors and matrices, you select elements from a data frame with the help of square brackets `[ ]`. By using a comma, you can indicate what to select from the rows and the columns respectively. For example:

- `my_data_frame[1,2]` selects from the first row in `my_data_frame`, the second element.
- `my_data_frame[1:3,2:4]` selects rows 1,2,3 and columns 2,3,4 in `my_data_frame`.

Sometimes you want to select all elements of a row or column. In that case, you just don't put anything in front or behind the comma: e.g. `my_data_frame[1,]` selects all elements of the first row. Let's now apply this technique on `planets_df`!

*** =instructions
	- Create the data frame `closest_planets_df` containing all data on the first three planets.
	- Create the data frame `furthest_planets_df` containing all data on the last three planets.

*** =hint
`planets_df[1:3,]` will select alle elements of the first three rows.

*** =sample_code


```r
# The planets_df data frame from the previous exercise is pre-loaded
closest_planets_df = 
furthest_planets_df = 
# Have a look:
closest_planets_df
furthest_planets_df
```


*** =solution


```r
# The planets_df data frame from the previous exercise is pre-loaded
closest_planets_df = planets_df[1:3, ]

furthest_planets_df = planets_df[6:8, ]

# Have a look:
closest_planets_df
furthest_planets_df
```


*** =sct


```r
if (!exists("closest_planets_df")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'closest_planets_df'.")
} else if (!isTRUE(try(all.equal(closest_planets_df, planets_df[1:3, ])))) {
    DM.result = list(FALSE, "Did you select the first three rows of 'planets_df'?")
} else if (!exists("furthest_planets_df")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'furthest_planets_df'.")
} else if (!isTRUE(try(all.equal(furthest_planets_df, planets_df[6:8, ])))) {
    DM.result = list(FALSE, "Make sure you select the last three rows of 'planets_df'.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code


```r
planets = c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", 
    "Neptune")
type = c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
    "Gass giant", "Gass giant", "Gass giant", "Gass giant")
diameter = c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation = c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings = c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

planets_df = data.frame(type, planets, diameter, rotation, rings)
```



---

## Selection of data frame elements (2)

Instead of using numerics to select elements of a data frame, you can also use the variable names to select columns of a data frame. 

Maybe you want to select only the first 3 elements of the variable 'type'. One way to do this is: `planets_df[1:3,1]`. A possible disadvantage of this approach is that you have to know (or look up) the position of the variable 'type', which gets hard if you have a lot of variables. It is often easier just to make use of the variable name, e.g. `planets_df[1:3,"type"]`.

*** =instructions
	- Select for the last six rows only the diameter and assign this selection to `furthest_planets_diameter`.

*** =hint
You select elements of a data frame conveniently with the square brackets. Select `3:8` for the rows, and `"diameter"` for the columns.

*** =sample_code


```r
# The planets_df data frame from the previous exercise is pre-loaded: 
furthest_planets_diameter = 
```


*** =solution


```r
# The planets_df data frame from the previous exercise is pre-loaded
furthest_planets_diameter = planets_df[3:8, "diameter"]
```


*** =sct


```r
if (!exists("furthest_planets_diameter")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'furthest_planets_diameter'.")
} else if (!isTRUE(try(all.equal(furthest_planets_diameter, planets_df[3:8, 
    "diameter"])))) {
    DM.result = list(FALSE, "Make sure you select the last six rows and only the 'diameter' column.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code


```r
planets = c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", 
    "Neptune")
type = c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
    "Gass giant", "Gass giant", "Gass giant", "Gass giant")
diameter = c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation = c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings = c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

planets_df = data.frame(type, planets, diameter, rotation, rings)
```


---

## Only planets with rings

You'll often want to select an entire column, i.e. 1 specific variable from a data frame. Suppose you want to select all elements of the variable `rings`: both `planets_df[,5]` and `planets_df[,"rings"]` do the trick. 

However, there is a short-cut. Use the `$`-sign to tell R it only has to look up all the elements of the variable behind the sign: `data_frame_name$variable_name`.

*** =instructions
	- Make use of the `$` -sign to create the `rings_vector` that contains all elements of the 'rings' variable in the planets_df data frame.

*** =hint
`data_frame_name$variable_name` is the most convenient way to select a variable from a data frame. In this case the data frame of choice is `planets_df` and the variable of choice is `rings`.

*** =sample_code


```r
# Create the rings_vector
rings_vector = 
```


*** =solution


```r
# Create the rings_vector
rings_vector = planets_df$rings
```


*** =sct


```r
if (!exists("rings_vector")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'rings_vector'.")
} else if (!isTRUE(try(all.equal(rings_vector, planets_df$rings)))) {
    DM.result = list(FALSE, "Looks like 'rings_vector' doesn't contain all the element of the 'ring' variable of the 'planets_df'.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code


```r
planets = c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", 
    "Neptune")
type = c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
    "Gass giant", "Gass giant", "Gass giant", "Gass giant")
diameter = c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation = c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings = c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

planets_df = data.frame(type, planets, diameter, rotation, rings)
```



---

## Only planets with rings (2)

From highschool, you remember some planets in our solar system have rings and others don't. But due to other priorities at that time (read: puberty) you can't recall their names, let alone their rotation speed, etc. 


Could R help you out? (Spoiler alert: of course it can!) 

Mmm, type `rings_vector` in the console and you get: FALSE FALSE FALSE FALSE TRUE TRUE TRUE TRUE 

This means that the first 4 observations (or planets) do not have a ring (FALSE), but the other 4 do (TRUE). However, you don't get a nice overview of the names of these planets, their diameter, etc. As a next step, use `rings_vector` to select from `planets_df` all the data (i.e. all columns) on the four planets with rings.

*** =instructions
	- Assign to `planets_with_rings_df` all data in the planets_df dataset for the planets with rings (i.e. where `rings_vector` is TRUE).

*** =hint
Select elements from `planets_df` using the square brackets. The `rings_vector` contains boolean values and R will select only those rows/columns were the vector element is TRUE. In this case you want to select rows based on `rings_vector` and select all the columns.

*** =sample_code


```r
# Note that the planets_df dataset and rings_vector are pre-loaded in your workspace

# Select the information on planets with rings:
planets_with_rings_df = 
```


*** =solution


```r
# Note that the planets_df dataset and rings_vector are pre-loaded in your
# workspace

# Select the information on planets with rings:
planets_with_rings_df = planets_df[rings_vector, ]
```


*** =sct


```r
if (!exists("planets_with_rings_df")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'planets_with_rings_df'.")
} else if (!isTRUE(try(all.equal(planets_with_rings_df, planets_df[rings_vector, 
    ])))) {
    DM.result = list(FALSE, "Looks like 'planets_with_rings_df' doesn't contain all the data of the planets with rings.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code


```r
planets = c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", 
    "Neptune")
type = c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
    "Gass giant", "Gass giant", "Gass giant", "Gass giant")
diameter = c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation = c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings = c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

planets_df = data.frame(type, planets, diameter, rotation, rings)
rings_vector = planets_df$rings
```



---

## Only planets with rings but shorter

So what exactly did you learn in the past exercises? You selected a subset from a data frame ( `planets_df` ), based on whether or not a certain condition was true (rings or no rings), and you managed to pull out all relevant data. Pretty awesome! By now, NASA is probably already flirting with your CV ;-). 

Now, let's move up one level and use the function `subset()`. You should see the `subset()` function as a short-cut to do exactly the same as what you just did. 

`subset(data_frame_name, subset = some.condition)` 

The first argument of `subset()` specifies the dataset from which you want a subset. With the second argument, you give R the necessary information and conditions to select the correct subset. 
For example: `subset(planets_df, subset=(planets_df$rings == TRUE))` 

R will give you exactly the same result as you got in the previous exercise. But this time without needing the `rings_vector`!

*** =instructions
	- Create a dataframe `small_planets_df` with planets that have a diameter smaller than earth (i.e smaller than 1, since diameter is a relative measure of the planets diameter).

*** =hint
Sorry, you're on your own here.

*** =sample_code


```r
# Planets smaller than earth:
small_planets_df  = # Your code here!
```


*** =solution


```r
# Planets smaller than earth:
small_planets_df = subset(planets_df, subset = planets_df$diameter < 1)
```


*** =sct


```r
if (!exists("small_planets_df")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'small_planets_df'.")
} else if (!isTRUE(try(all.equal(small_planets_df, subset(planets_df, subset = planets_df$diameter < 
    1))))) {
    DM.result = list(FALSE, "Looks like 'small_planets_df' doesn't contain all the correct subset of planets_df.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code


```r
planets = c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", 
    "Neptune")
type = c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
    "Gass giant", "Gass giant", "Gass giant", "Gass giant")
diameter = c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation = c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings = c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

planets_df = data.frame(type, planets, diameter, rotation, rings)
```



---

## Sorting

Making and creating rankings, is one of mankinds favorite affairs. These rankings can be useful (best universities in the world), entertaining (most influencial moviestars) or pointless (best 007 look-a-like). Up to you for which purpose you want to use your R skills ;-). 

In data analysis you will sort your data according to a certain variable in the dataset. In R, this is done with the help of the function `order()`. 

`order()` is a function that, when applied on a variable, gives you in return the position of each element. Let's look at the vector `a`: `a = c(100,9,101)`. Now `order(a)` returns 2,1,3. Since 100 is the second largest element of the vector, 9 is the smallest element and 101 is the largest element.
    
Subsequently, `a[order(a)]` will give you the ordered vector 9,100,101, since it first picks the second element of a, then the first, then the last. Got it? If you're not sure, use the console to play with the `order()` function.` 

*** =instructions
	- Click Submit Answer when you are ready.

*** =hint
Just play with the `order()` function in the console!

*** =sample_code




*** =solution


```r
# Just play around with the order function in the console to see how it
# works Some examples:
order(1:10)
order(2:11)
order(c(5, 4, 6, 7))
```


*** =sct


```r
if (!isTRUE(try(student_typed("order(")))) {
    DM.result = list(FALSE, "Makse sure to use the 'order' function.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code





---

## Sorting your data frame

Alright, now that you understand the `order()` function, let's do something useful shall we? You'd like to rearrange your data frame such that it starts with the largest planet and ends with the smallest one (i.e. sort on the column diameter).

*** =instructions
	- Assign to the variable positions the desired ordering for the new data frame you will create in the next step. You can use the `order()` function for that, with the additional argument `decreasing=TRUE`.
	- Now create the data frame `largest_first_df`, wich contains the same information as `planets_df`, but with the planets in decreasing order of magnitude.

*** =hint
`order(planets_df$diameter, decreasing=TRUE)` will give you the ordering of the variable diameter from largest to smallest. This is wat you should assign to positions. Use the variable positions then to select from the data `frame planets_df` !

*** =sample_code


```r
#NOTE: The data frame planets_df has been pre-loaded

# What is the correct ordering based on the planets_df$diameter variable?
positions =  

# Create new "ordered" data frame:
largest_first_df =
```


*** =solution


```r
# NOTE: The data frame planets_df has been pre-loaded

# What is the correct ordering based on the planets_df$diameter variable?
positions = order(planets_df$diameter, decreasing = TRUE)

# Create new 'ordered' data frame:
largest_first_df = planets_df[positions, ]
```


*** =sct


```r
if (!exists("positions")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'positions'.")
} else if (!isTRUE(try(all.equal(positions, order(planets_df$diameter, decreasing = TRUE))))) {
    DM.result = list(FALSE, "Looks like 'positions' doesn't contain all the correct ordering of the diameter column.")
} else if (!exists("largest_first_df")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'largest_first_df'.")
} else if (!isTRUE(try(all.equal(largest_first_df, planets_df[positions, ])))) {
    DM.result = list(FALSE, "Looks like 'largest_first_df' doesn't contain the positions of the ordered 'planets_df'.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code


```r
planets = c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", 
    "Neptune")
type = c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
    "Gass giant", "Gass giant", "Gass giant", "Gass giant")
diameter = c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation = c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings = c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

planets_df = data.frame(type, planets, diameter, rotation, rings)
```


