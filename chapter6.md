--- 
title_meta  : Chapter 6
title       : Lists
description : List have components of different types just like your to-do list at home or at work. Learn how to create, name and subset in this chapter!
framework   : datacamp
mode        : selfcontained

---

## Lists, why would you need them?

Congratulations! At this point in the course you are alreade a (semi-)expert in:

- **Vectors** (one dimensional array) Holds numeric, character or logical values. The elements in one vector all have the same datatype.
- **Matrices** (two dimensional array) Holds numeric, character or logical values. The elements in one matrix all have the same datatype.
- **Data frames** (two-dimensional objects) Holds numeric, character or logical values. Within a column all elements have the same datatype, but between columns not necessarily.

Pretty sweet for an R newbie don't you think? ;-)

*** =instructions
	- Click Submit Answer to start learning everything about lists!

*** =hint
Just click the Run button.

*** =sample_code


```r
# Just click the Run button!
```


*** =solution


```r
# Just click the Run button.
```


*** =sct


```r
DM.result = list(TRUE, "Great! Continue to the next exercise.")
```


*** =pre_exercise_code





---

## Lists, why would you need them? (2)

A **list** in R is similar to your to-do list at work or school: The different items on your to-do list most likely differ in length, characteristic, type of to do... 

A list in R allows you to gather a variety of objects under one name (the name of the list) in an ordered way. These objects can be matrices, vectors, data frames, even other lists, etc. It is not even required these objects are related to each other. Just like with your to-do list :-). 

Maybe you can even say that a list is a kind of super data type ;-)

*** =instructions
	- Click Submit Answer to start the first exercise on lists.

*** =hint
Click Run to start the first exercise on lists.

*** =sample_code


```r
# Click Run to start the first exercise on lists.
```


*** =solution


```r
# Click Submit Answer to start the first exercise on lists.
```


*** =sct


```r
DM.result = list(TRUE, "Great! Continue to the next exercise.")
```


*** =pre_exercise_code





---

## Creating a list

Let's create our first list! To construct a list you use the function `list()`: 

`my_list = list(component1, component2...)`

The arguments to the list function are the list components. Remember, these components can be a  collection of matrices, vectors...` 

*** =instructions
	- Construct a list with `my_vector`, `my_matrix` and `my_df` as list components.

*** =hint
Just use the `list()` function with `my_vector`, `my_matrix` and `my_df` as arguments separated by a comma.

*** =sample_code


```r
# Vector with numerics from 1 up to 10
my_vector = 1:10 
# Matrix with numerics from 1 up to 9
my_matrix = matrix(1:9, ncol=3)
# First 10 elements of the built-in data frame mtcars
my_df     = mtcars[1:10,] 

# Construct list with these different elements:
my_list = 
```


*** =solution


```r
# Vector with numerics from 1 up to 10
my_vector = 1:10
# Matrix with numerics from 1 up to 9
my_matrix = matrix(1:9, ncol = 3)
# First 10 elements of the built-in data frame mtcars
my_df = mtcars[1:10, ]

# Construct list with these different elements:
my_list = list(my_vector, my_matrix, my_df)
```


*** =sct


```r
if (!exists("my_list")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'my_list'.")
} else if (!isTRUE(try(all.equal(my_list, list(my_vector, my_matrix, my_df))))) {
    DM.result = list(FALSE, "Looks like 'my_list' doesn't contain the correct elements.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code





---

## Creating a named list

Well done! Let's keep this train going! 

Like on your to-do list, you want to avoid not knowing (or remembering) what the components of your to-do list stand for. That is why you should give names to them: 

`list(name1=your.component1, name2=component2,?)` 

This creates for you a list with the components `"name1"` and `"name2"` and so on.

*** =instructions
	- Change the code of the previous exercise (see editor) by adding names to the components. Use for `my_matrix` the name `MATRIX`, for `my_vector` `VECTOR` and for `my_df` `DATAFRAME`. Look at the console output to see how R prints a list.

*** =hint
No hints, you can do this!

*** =sample_code


```r
# Vector with numerics from 1 up to 10
my_vector = 1:10
# Matrix with numerics from 1 up to 9
my_matrix = matrix(1:9, ncol = 3)
# First 10 elements of the built-in data frame mtcars
my_df = mtcars[1:10, ]

# Construct list with these different elements:
my_list = list(my_vector, my_matrix, my_df)
```


*** =solution


```r
# Vector with numerics from 1 up to 10
my_vector = 1:10
# Matrix with numerics from 1 up to 9
my_matrix = matrix(1:9, ncol = 3)
# First 10 elements of the built-in data frame mtcars
my_df = mtcars[1:10, ]

# Construct list with these different elements:
my_list = list(VECTOR = my_vector, MATRIX = my_matrix, DATAFRAME = my_df)
```


*** =sct


```r
if (!exists("my_list")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'my_list'.")
} else if (!isTRUE(try(all.equal(my_list, list(VECTOR = my_vector, MATRIX = my_matrix, 
    DATAFRAME = my_df))))) {
    DM.result = list(FALSE, "Looks like 'my_list' doesn't contain the correct naming for the components.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code





---

## Creating a named list (2)

Being a huge movie fan (remember your job @ LucasFilms), you decide to start storing information on good movies with the help of lists. 

Start by creating a list for the movie "The Shining". We already created the variables `actors` and `reviews` in your R workspace. Type `actors` or `reviews` in the console to check these.

*** =instructions
	- Create the variable `shining_list`. The list contains the following components:
  	- moviename: "The Shining"
  	- actors: a vector with main actors names
  	- reviews: a data frame containing some reviews

Do not forget to name the list components accordingly!

*** =hint
No hints, you can do this!

*** =sample_code


```r
# Create the named vector shining_list
# The actors and reviews vectors are loaded in the workspace
shining_list = 
```


*** =solution


```r
# Create the shining_list The actors and reviews vectors are loaded in the
# workspace
shining_list = list(moviename = "The Shining", actors = actors, reviews = reviews)
```


*** =sct


```r
if (!exists("shining_list")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'shining_list'.")
} else if (!isTRUE(try(all.equal(shining_list, list(moviename = "The Shining", 
    actors = actors, reviews = reviews))))) {
    DM.result = list(FALSE, "Looks like 'shining_list' doesn't contain the correct components.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code


```r
actors = c("Jack Nicholson", "Shelley Duvall", "Danny Lloyd", "Scatman Crothers", 
    "Barry Nelson")
sources = c("IMDb1", "IMDb2", "IMDB3")
comments = c("Best Horror Film I've Ever Seen", "A truly brilliant and scary film from Stanley Kubrick", 
    "A masterpiece of psychological horror")
scores = c(4.5, 4, 5)
reviews = data.frame(scores, sources, comments)
```



---

## Selecting elements from a list

Often, your list will be build out of numerous elements and components. Therfore, getting a single element, multiple elements, or a component out of it is not always straightforward. 

One way to select a component, is using the numbered position of that component. For example, to "grab" the first component of `shining_list` you type `shining_list[[1]]`. (Remember, to select elements out of a data set you use square brackets `[ ]` ) A quick way to check this out is by typing it in the console. 

Another way is referring to the names of the components. `shining_list[["reviews"]]` selects the `reviews` data frame. The same is true for the shorter version `shining_list$reviews`. 

Besides selecting components, you often need to select specific elements out of these components. For example, with `shining_list[[2]][1]` you select from the second component actors (= `shining_list[[2]]` ) the first element ( `[1]` ). When you type this in the console, you will see the answer is Jack Nicholson.

*** =instructions
	- Select from the `shining_list` the last actor and assign to the `last_actor`.
	- Select from the `shining_list` all information regarding the second review.

*** =hint
	- If you want to do things nicely: `length(shining_list$actors])` gives you the number of actors, and thus the element to select.
	- You can select the information of the second review with `shining_list$reviews[2,]`.

*** =sample_code


```r
# The shining_list is already loaded
# Select from the shining_list:
last_actor    = 
second_review = 
```


*** =solution


```r
# The shining_list is already loaded Select from the shining_list:
last_actor = shining_list$actors[length(shining_list$actors)]
second_review = shining_list$reviews[2, ]
```


*** =sct


```r
if (!exists("last_actor")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'last_actor'.")
} else if (!isTRUE(try(all.equal(last_actor, shining_list$actors[length(shining_list$actors)])))) {
    DM.result = list(FALSE, "Looks like 'last_actor' doesn't equal the last actor.")
} else if (!exists("second_review")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'second_review'.")
} else if (!isTRUE(try(all.equal(second_review, shining_list$reviews[2, ])))) {
    DM.result = list(FALSE, "Looks like 'second_review' doesn't contain all the information regarding the second review.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code


```r
actors = c("Jack Nicholson", "Shelley Duvall", "Danny Lloyd", "Scatman Crothers", 
    "Barry Nelson")
sources = c("IMDb1", "IMDb2", "IMDB3")
comments = c("Best Horror Film I've Ever Seen", "A truly brilliant and scary film from Stanley Kubrick", 
    "A masterpiece of psychological horror")
scores = c(4.5, 4, 5)
reviews = data.frame(scores, sources, comments)
shining_list = list(moviename = "The Shining", actors = actors, reviews = reviews)
```



---

## Adding more movie information to the list

Being proud of your first list, you shared it with the members of your movie hobby club. However, one of the senior members (a guy named M. McDowell) noted you forgot to add the release year. Given your ambitions to become next years president of the club, you decide to add this info to the list. 

To conviently add elements to lists, you use the concatenate function `c()`: 

`c(list1,some.object)` 

If you want to give the new list item a name, you just add this to the function: `c(list1,new.item.name=some.object)`.

*** =instructions
	- Complete the code below such that an item named `year` is added to the `shining_list` with the value 1980.

*** =hint
You're on your own now!

*** =sample_code


```r
actors = c("Jack Nicholson", "Shelley Duvall", "Danny Lloyd", "Scatman Crothers", 
    "Barry Nelson")
sources = c("IMDb1", "IMDb2", "IMDB3")
comments = c("Best Horror Film I've Ever Seen", "A truly brilliant and scary film from Stanley Kubrick", 
    "A masterpiece of psychological horror")
scores = c(4.5, 4, 5)
reviews = data.frame(scores, sources, comments)

# Create named list
shining_list = list(moviename = "The Shining", actors = actors, reviews = reviews)

# We forgot something: Add the year to shining_list ! Add your code below:
shining_list = 
# Have a look at shining_list.
str(shining_list)
```


*** =solution


```r
actors = c("Jack Nicholson", "Shelley Duvall", "Danny Lloyd", "Scatman Crothers", 
    "Barry Nelson")
sources = c("IMDb1", "IMDb2", "IMDB3")
comments = c("Best Horror Film I've Ever Seen", "A truly brilliant and scary film from Stanley Kubrick", 
    "A masterpiece of psychological horror")
scores = c(4.5, 4, 5)
reviews = data.frame(scores, sources, comments)

# Create named list
shining_list = list(moviename = "The Shining", actors = actors, reviews = reviews)

# We forgot something: Add the year to shining_list !
shining_list = c(shining_list, year = 1980)

# Have a look at shining_list.
str(shining_list)
```


*** =sct


```r
if (!exists("shining_list")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'shining_list'.")
} else if (!isTRUE(try(all.equal(shining_list, list(moviename = "The Shining", 
    actors = actors, reviews = reviews, year = 1980))))) {
    DM.result = list(FALSE, "Looks like 'shining_list' doesn't contain the year item.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code



