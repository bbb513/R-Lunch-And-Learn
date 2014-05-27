--- 
title_meta  : Chapter 3
title       : Matrices
description : In this chapter, you'll learn how to work with matrices in R. By the end of the chapter you'll be able to create matrices, and understand how you can do basic computations with them. You'll analyze the box office numbers of Star Wars to illustrate the use of matrices in R. May to force be with you! 
framework   : datacamp
mode        : selfcontained

---


## What's a matrix?

In R, a matrix is a collection of elements of the same data type (numeric, character, or logical) arranged into a fixed number of rows and columns. Since you are only working with rows and columns, a matrix is called two-dimensional. 

In R, you can construct a matrix with the `matrix` function, for example: `matrix(1:9, byrow=TRUE, nrow=3)`:
- The first argument, is the collection of elements that R will arrange into the rows and columns of the matrix. Here, we use `1:9` which constructs the vector `c(1,2,3,4,5,6,7,8,9)`. 
- The argument `byrow` indicates that the matrix is filled by the rows. If we want the vector to be filled by the columns, we just place `bycol=TRUE` or `byrow=FALSE`. 
- The third argument `nrow` indicates that the matrix should have three rows.

*** =instructions
	- Construct a matrix with 3 rows containing the numbers 1 up to 9. Click the Submit Answer button and look at the output in the console. Hint, use: `matrix(1:9, byrow=TRUE, nrow=3)`.

*** =hint
Read the assignment carefully, the answer is already given ;-).

*** =sample_code


```r
# Construction of a matrix with 3 rows containing the numbers 1 up to 9
```


*** =solution


```r
# Construction of a matrix with 3 rows containing the numbers 1 up to 9
matrix(1:9, byrow = TRUE, nrow = 3)
```


*** =sct


```r
if (!(isTRUE(try(output_contains("matrix(1:9, byrow=TRUE, nrow=3)")))){
	DM.result = list(FALSE, "There seems to be an issue with the matrix definition.");
} else {
	DM.result = list(TRUE, "Great! Continue to the next exercise.");
}
```


*** =pre_exercise_code





---

## Analyzing matrices, you shall

It is time to get your hands dirty. In the following exercises you will analyze the box office numbers of the Star Wars franchisee. May the force be with you! 

In the editor, three vectors are defined each representing the box office numbers from the first three Star Wars movies. The first element of each vector indicates the US box office revenue, the second element refers to the Non-US box office (source: Wikipedia).

*** =instructions
	- Construct a matrix with one row for each movie (thus 3 rows). The first column is for the US box office revenue, and the second column for the non-US box office revenue. Name the matrix `star_wars_matrix`.

*** =hint
Remember that you can construct a matrix containing the numbers 1 up to 9 with: `matrix(1:9, byrow=TRUE, nrow=3)`. In this case, you don't want the numbers 1 up to 9, but the elements of the 3 Star Wars movies: this means the input vector is thus: `c(new_hope,empire_strikes,return_jedi)`.

*** =sample_code


```r
# Box office Star Wars: In Millions!
# The first element: US, the second element: Non-US 
new_hope 				= c(460.998007, 314.4)
empire_strikes 	= c(290.475067, 247.900000)
return_jedi 		= c(309.306177,165.8)

# Add your code below to construct the matrix
star_wars_matrix = 
```


*** =solution


```r
# Box office Star Wars: In Millions!  The first element: US, Second element:
# Non-US
new_hope = c(460.998007, 314.4)
empire_strikes = c(290.475067, 247.9)
return_jedi = c(309.306177, 165.8)

# Add your code below to construct the matrix
star_wars_matrix = matrix(c(new_hope, empire_strikes, return_jedi), nrow = 3, 
    byrow = TRUE)
```


*** =sct


```r
if (!exists("new_hope")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'new_hope'.")
} else if (!isTRUE(try(all.equal(new_hope, c(460.998007, 314.4))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'new_hope' to the correct vector.")
} else if (!exists("empire_strikes")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'empire_strikes'.")
} else if (!isTRUE(try(all.equal(empire_strikes, c(290.475067, 247.9))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'empire_strikes' to the correct vector.")
} else if (!exists("return_jedi")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'return_jedi'.")
} else if (!isTRUE(try(all.equal(return_jedi, c(309.306177, 165.8))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'return_jedi' to the correct vector.")
} else if (!exists("star_wars_matrix")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'star_wars_matrix'.")
} else if (!isTRUE(try(all.equal(star_wars_matrix, matrix(c(new_hope, empire_strikes, 
    return_jedi), nrow = 3, byrow = TRUE))))) {
    DM.result = list(FALSE, "Did you assign to 'star_wars_matrix' to the correct matrix containing the vector that holds all three movies?")
} else {
    DM.result = list(TRUE, "Good! Continue to the next exercise.")
}
```


*** =pre_exercise_code




---

## Naming a matrix

To help you remember what's stored in `star_wars_matrix`, you'd like to add the names of the movies for the rows. Not only does this helps you to read the data, it is also useful to select certain elements from the matrix later. 

Similar to vectors, you can add names for the rows and the columns of a matrix with:

- `rownames(my_matrix) = row_names_vectors`
- `colnames(my_matrix) = col_names_vectors`


*** =instructions
	- Give the columns of `star_wars_matrix` the names `"US"` and `"non-US"`.
	- Give the rows of the matrix `star_wars_matrix` the names of the three movies. In case you are not a fan ;-), the movie names are: "A new hope", "The empire strikes back" and "Return of the Jedi".


*** =hint
Don't forget that R is case sensitive. The vector for the column names is thus: `c("US","non-US")` and for the row names: `c("A new hope","The empire strikes back","Return of the Jedi")`.

*** =sample_code


```r
# Box office Star Wars: In Millions (!)  First element: US, Second element:
# Non-US
new_hope = c(460.998007, 314.4)
empire_strikes = c(290.475067, 247.9)
return_jedi = c(309.306177, 165.8)

# Construct matrix
star_wars_matrix = matrix(c(new_hope, empire_strikes, return_jedi), nrow = 3, 
    byrow = TRUE)

# Add your code here such that rows and columns of star_wars_matrix have a
# name!

```


*** =solution


```r
# Box office Star Wars: In Millions (!)  First element: US, Second element:
# Non-US
new_hope = c(460.998007, 314.4)
empire_strikes = c(290.475067, 247.9)
return_jedi = c(309.306177, 165.8)

# Construct matrix
star_wars_matrix = matrix(c(new_hope, empire_strikes, return_jedi), nrow = 3, 
    byrow = TRUE)

# Add your code here such that rows and columns of star_wars_matrix have a
# name!
colnames(star_wars_matrix) = c("US", "non-US")
rownames(star_wars_matrix) = c("A new hope", "The empire strikes back", "Return of the Jedi")
```


*** =sct


```r
if (!exists("new_hope")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'new_hope'.")
} else if (!isTRUE(try(all.equal(new_hope, c(460.998007, 314.4))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'new_hope' to the correct vector.")
} else if (!exists("empire_strikes")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'empire_strikes'.")
} else if (!isTRUE(try(all.equal(empire_strikes, c(290.475067, 247.9))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'empire_strikes' to the correct vector.")
} else if (!exists("return_jedi")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'return_jedi'.")
} else if (!isTRUE(try(all.equal(return_jedi, c(309.306177, 165.8))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'return_jedi' to the correct vector.")
} else if (!exists("star_wars_matrix")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'star_wars_matrix'.")
} else if (!isTRUE(try(all.equal(star_wars_matrix, matrix(c(new_hope, empire_strikes, 
    return_jedi), nrow = 3, byrow = TRUE))))) {
    DM.result = list(FALSE, "Did you assign to 'star_wars_matrix' to the correct matrix containing the vector that holds all three movies?")
} else if (!isTRUE(try(all.equal(colnames(star_wars_matrix), c("US", "non-US"))))) {
    DM.result = list(FALSE, "Did you set the column names of 'star_wars_matrix' to the correct vector?")
} else if (!isTRUE(try(all.equal(rownames(star_wars_matrix), c("A new hope", 
    "The empire strikes back", "Return of the Jedi"))))) {
    DM.result = list(FALSE, "Did you set the rownames names of 'star_wars_matrix' to the correct vector?")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code





---

## Calculating the worldwide box office 

The single most important thing for a movie to become an instant legend in Tinseltown is its worldwide box office figures. 

To calculate the total box office revenue for the three Star Wars movies, you have to take the sum of the US revenue column and the non-US revenue column. 

In R, the function `rowSums()` conveniently calculates the totals for each row of a matrix. This function creates a new vector. `sum_of_rows_vector =  rowSums(my_matrix)`.

*** =instructions
	- Calculate the worldwide box office figures for the three movies and put these in the vector named `worldwide_vector`.

*** =hint
The `rowSums()` function will calculate the total box office for each row of the `star_wars_matrix`, if you supply `star_wars_matrix` as an argument to that function by putting it between the brackets.

*** =sample_code


```r
# Box office Star Wars: In Millions (!) 
# Construct matrix: 
box_office_all 				= c(461, 314.4,290.5, 247.9,309.3,165.8)
movie_names    				= c("A new hope","The empire strikes back","Return of the Jedi")
col_titles     				= c("US","non-US")
star_wars_matrix      = matrix(box_office_all, nrow=3, byrow=TRUE, dimnames=list(movie_names,col_titles))

# Your code here
worldwide_vector = 
```


*** =solution


```r
# Box office Star Wars: In Millions (!)  Construct matrix:
box_office_all = c(461, 314.4, 290.5, 247.9, 309.3, 165.8)
movie_names = c("A new hope", "The empire strikes back", "Return of the Jedi")
col_titles = c("US", "non-US")
star_wars_matrix = matrix(box_office_all, nrow = 3, byrow = TRUE, dimnames = list(movie_names, 
    col_titles))

# Your code here
worldwide_vector = rowSums(star_wars_matrix)
```


*** =sct


```r
if (!exists("box_office_all")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'box_office_all'.")
} else if (!isTRUE(try(all.equal(box_office_all, c(461, 314.4, 290.5, 247.9, 
    309.3, 165.8))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'box_office_all' to the correct vector.")
} else if (!exists("movie_names")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'movie_names'.")
} else if (!isTRUE(try(all.equal(movie_names, c("A new hope", "The empire strikes back", 
    "Return of the Jedi"))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'movie_names' to the correct vector.")
} else if (!exists("col_titles")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'col_titles'.")
} else if (!isTRUE(try(all.equal(col_titles, c("US", "non-US"))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'col_titles' to the correct vector.")
} else if (!exists("star_wars_matrix")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'star_wars_matrix'.")
} else if (!isTRUE(try(all.equal(star_wars_matrix, matrix(box_office_all, nrow = 3, 
    byrow = TRUE, dimnames = list(movie_names, col_titles)))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'star_wars_matrix' to the correct vector.")
} else if (!exists("worldwide_vector")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'worldwide_vector'.")
} else if (!isTRUE(try(all.equal(worldwide_vector, rowSums(star_wars_matrix))))) {
    DM.result = list(FALSE, "Did you use the 'rowSums() function on the correct vector?'")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code





---

## Adding a column for the Worlwide box office 

In the previous exercise, you calculated the vector that contained the worldwide box office receipt for each of the three Star Wars movies. However, this vector is not yet part of `star_wars_matrix`...

You can add a column or multiple columns to a matrix with the `cbind` function, which merges matrices and/or vectors together by column. For example: `new_combined_matrix = cbind( matrix1, matrix2, vector1, ... )`.

*** =instructions
	- Add `worldwide_vector` as a new column to the `star_wars_matrix` and assign to `all_wars_matrix`. Use the `cbind()` function.

*** =hint
Bind the `worldwide_vector` to the `star_wars_matrix` with the `cbind()` function, with `cbind( the_correct_matrix, the_correct_vector)` and assign to `all_star_wars_matrix`.

*** =sample_code


```r
# Box office Star Wars: In Millions (!) 
# Construct matrix
box_office_all 				= c(461, 314.4,290.5, 247.9,309.3,165.8)
movie_names 					= c("A new hope","The empire strikes back","Return of the Jedi")
col_titles  					= c("US","non-US")
star_wars_matrix 			= matrix(box_office_all, nrow=3, byrow=TRUE, dimnames=list(movie_names,col_titles))

# The worldwide box office figures
worldwide_vector = rowSums(star_wars_matrix)

# Bind the new variable worldwide_vector as a column to star_wars_matrix
all_wars_matrix = 
```


*** =solution


```r
# Box office Star Wars: In Millions (!)  Construct matrix
box_office_all = c(461, 314.4, 290.5, 247.9, 309.3, 165.8)
movie_names = c("A new hope", "The empire strikes back", "Return of the Jedi")
col_titles = c("US", "non-US")
star_wars_matrix = matrix(box_office_all, nrow = 3, byrow = TRUE, dimnames = list(movie_names, 
    col_titles))

# The worldwide box office figures
worldwide_vector = rowSums(star_wars_matrix)

# Bind the new variable worldwide_vector as a column to star_wars_matrix
all_wars_matrix = cbind(star_wars_matrix, worldwide_vector)
```


*** =sct


```r
if (!exists("box_office_all")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'box_office_all'.")
} else if (!isTRUE(try(all.equal(box_office_all, c(461, 314.4, 290.5, 247.9, 
    309.3, 165.8))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'box_office_all' to the correct vector.")
} else if (!exists("movie_names")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'movie_names'.")
} else if (!isTRUE(try(all.equal(movie_names, c("A new hope", "The empire strikes back", 
    "Return of the Jedi"))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'movie_names' to the correct vector.")
} else if (!exists("col_titles")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'col_titles'.")
} else if (!isTRUE(try(all.equal(col_titles, c("US", "non-US"))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'col_titles' to the correct vector.")
} else if (!exists("star_wars_matrix")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'star_wars_matrix'.")
} else if (!isTRUE(try(all.equal(star_wars_matrix, matrix(box_office_all, nrow = 3, 
    byrow = TRUE, dimnames = list(movie_names, col_titles)))))) {
    DM.result = list(FALSE, "Make sure that you assign to 'star_wars_matrix' to the correct vector.")
} else if (!exists("worldwide_vector")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'worldwide_vector'.")
} else if (!isTRUE(try(all.equal(worldwide_vector, rowSums(star_wars_matrix))))) {
    DM.result = list(FALSE, "Did you use the 'rowSums() function on the correct vector?'")
} else if (!exists("all_wars_matrix")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'all_wars_matrix'.")
} else if (!isTRUE(try(all.equal(all_wars_matrix, cbind(star_wars_matrix, worldwide_vector))))) {
    DM.result = list(FALSE, "Did you use the 'cbind() function with the correct arguments?'")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code




---

## Adding a row

Just like every action has a reaction, every `cbind()` has a `rbind()`. (Okay, we admit, we are pretty bad with metaphors.) 

Your R workspace ([check out what a workspace is](http://www.statmethods.net/interface/workspace.html)) now contains two matrices, the `star_wars_matrix` we just used (the first trilogy) but also the `star_wars_matrix2` for the second trilogy. Type the name of the matrices in the console and press enter in case you want to have a closer look.

*** =instructions
	- Assign to `all_wars_matrix` a new matrix with `star_wars_matrix` in the first three rows and `star_wars_matrix2` in the next three rows.

*** =hint
Bind the two matrices together in the following way: `rbind( matrix1, matrix2 )` and assign to `all_wars_matrix`.

*** =sample_code


```r
# Box office Star Wars: In Millions (!) 

# Matrix containing first trilogy box office
star_wars_matrix  

# Matrix containing second trilogy box office
star_wars_matrix2 

# Combine the both Star Wars trilogies in one matrix
all_wars_matrix = 
```


*** =solution


```r
# Box office Star Wars: In Millions (!)

# Matrix containing first trilogy box office
star_wars_matrix

# Matrix containing second trilogy box office
star_wars_matrix2

# Combine the both Star Wars trilogies in one matrix
all_wars_matrix = rbind(star_wars_matrix, star_wars_matrix2)
```


*** =sct


```r
if (!exists("all_wars_matrix")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'all_wars_matrix'.")
} else if (!isTRUE(try(all.equal(all_wars_matrix, rbind(star_wars_matrix, star_wars_matrix2))))) {
    DM.result = list(FALSE, "Did you use the 'rbind() function with the correct arguments?'")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code


```r
# Construct matrix
box_office_all = c(461, 314.4, 290.5, 247.9, 309.3, 165.8)
movie_names = c("A new hope", "The empire strikes back", "Return of the Jedi")
col_titles = c("US", "non-US")
star_wars_matrix = matrix(box_office_all, nrow = 3, byrow = TRUE, dimnames = list(movie_names, 
    col_titles))

# Construct matrix2
box_office_all2 = c(474.5, 552.5, 310.7, 338.7, 380.3, 468.5)
movie_names2 = c("The Phantom Menace", "Attack of the Clones", "Revenge of the Sith")
star_wars_matrix2 = matrix(box_office_all2, nrow = 3, byrow = TRUE, dimnames = list(movie_names2, 
    col_titles))
```



---

## The total box office revenue for the entire saga

Just like every `cbind()` has a `rbind()`, every `colSums()` has a `rowSums()`. Your R workspace contains the `all_wars_matrix` you constructed in the previous exercise (Type `all_wars_matrix` in the console if you don't recall what it contains). Let's now calculate the total box office revenue for the entire saga.

*** =instructions
	- Calculate the total revenue for the US and the non-US region and assign `total_revenue_vector`. You can use the `colSums()` function.

*** =hint
You should use the `colSums()` function with `star_wars_matrix` as argument to find the total box office per region.

*** =sample_code


```r
# Print box office Star Wars: In Millions (!) for 2 trilogies
all_wars_matrix

total_revenue_vector = 
```


*** =solution


```r
# Print box office Star Wars: In Millions (!) for 2 trilogies
all_wars_matrix

total_revenue_vector = colSums(all_wars_matrix)
```


*** =sct


```r
if (!exists("total_revenue_vector")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'total_revenue_vector'.")
} else if (!isTRUE(try(all.equal(total_revenue_vector, colSums(all_wars_matrix))))) {
    DM.result = list(FALSE, "Did you use the 'colSums() function on the all_wars_matrix?'")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code


```r
# Construct matrix
box_office_all = c(461, 314.4, 290.5, 247.9, 309.3, 165.8)
movie_names = c("A new hope", "The empire strikes back", "Return of the Jedi")
col_titles = c("US", "non-US")
star_wars_matrix = matrix(box_office_all, nrow = 3, byrow = TRUE, dimnames = list(movie_names, 
    col_titles))

# Construct matrix2
box_office_all2 = c(474.5, 552.5, 310.7, 338.7, 380.3, 468.5)
movie_names2 = c("The Phantom Menace", "Attack of the Clones", "Revenge of the Sith")
star_wars_matrix2 = matrix(box_office_all2, nrow = 3, byrow = TRUE, dimnames = list(movie_names2, 
    col_titles))

# Combine the both Star Wars trilogies in one matrix
all_wars_matrix = rbind(star_wars_matrix, star_wars_matrix2)
```



---

## Selection of matrix elements

Similar to vectors, use the square brackets `[ ]` to select one or multiple elements from a matrix. Whereas vectors have 1 dimension, matrices have 2 dimensions, therefore use a comma to separate what to select from the rows and what from the columns. For example: 
- `my_matrix[1,2]` selects from the first row the second element.
- `my_matrix[1:3,2:4]` selects rows 1,2,3 and columns 2,3,4.

If you want to select all elements of a row or column, no number is needed before or after the comma:
- `my_matrix[,1]` selects all elements of the first column.
- `my_matrix[1,]` selects all elements of the first row.

Back to Star Wars with this newly acquired knowledge!

*** =instructions
	- Calculate the average Non-US revenue per movie. Assign this to the `non_us_all` variable (In other words: take the average of all elements of the second column).
	- Same question, but now only for the first two Star Wars movies.

Hint: Use the function `mean()` to compute the average.

*** =hint
You can use the function `mean()` to calculate the average of the inputs to the function. Remember that you can select all rows of a matrix for a specific column x, by typing `my_matrix[,x]`. Non-US is the second column.

*** =sample_code


```r
# Box office Star Wars: In Millions (!) 
# Construct matrix 
box_office_all 			= c(461, 314.4,290.5, 247.9,309.3,165.8)
movie_names    			= c("A new hope","The empire strikes back","Return of the Jedi")
col_titles     			= c("US","non-US")
star_wars_matrix  	= matrix(box_office_all, nrow=3, byrow=TRUE, dimnames=list(movie_names,col_titles)) 

star_wars_matrix 

# your code here
non_us_all  =   
# your code here
non_us_some = 
```


*** =solution


```r
# Box office Star Wars: In Millions (!)  Construct matrix:
box_office_all = c(461, 314.4, 290.5, 247.9, 309.3, 165.8)
movie_names = c("A new hope", "The empire strikes back", "Return of the Jedi")
col_titles = c("US", "non-US")
star_wars_matrix = matrix(box_office_all, nrow = 3, byrow = TRUE, dimnames = list(movie_names, 
    col_titles))

star_wars_matrix

# your code here
non_us_all = mean(star_wars_matrix[, 2])
# your code here
non_us_some = mean(star_wars_matrix[1:2, 2])
```


*** =sct


```r
if (!exists("star_wars_matrix")){
  DM.result = list(FALSE, "Please make sure to define a variable 'star_wars_matrix'.");
} else if (!isTRUE(try(all.equal(star_wars_matrix,matrix(box_office_all, nrow=3, byrow=TRUE, dimnames=list(movie_names,col_titles)))))){
  DM.result = list(FALSE, "The 'star_wars_matrix' contains a wrong value.");
} if (!exists("non_us_all")){
  DM.result = list(FALSE, "Please make sure to define a variable 'non_us_all'.");
} else if (!isTRUE(try(all.equal(non_us_all,mean(star_wars_matrix[,2]))))){
  DM.result = list(FALSE, "Did you assign to 'non_us_all' the mean of the correct sub vector?");
} else if (!exists("non_us_some")){
  DM.result = list(FALSE, "Please make sure to define a variable 'non_us_some'.");
} else if (!isTRUE(try(all.equal(non_us_some,mean(star_wars_matrix[1:2,2]))))){
  DM.result = list(FALSE, "Did you assign to 'non_us_some' the mean of the correct sub vector?");
} else {
	DM.result = list(TRUE, "Great! Continue to the next exercise.");
}
```


*** =pre_exercise_code




---

## A little arithmetic with matrices

Similar to what you learned with vectors, the standard operators like `+`, `-`, `/`, `*`, etc. work in an element-wise way on matrices in R. 

For example: `2*my_matrix` multiplies each element of `my_matrix` by two. 

As a newly-hired data analyst for Lucasfilm, your job is to find out how many visitors went to each movie for each geographical area. You already have the total revenue figures in `star_wars_matrix`. Assume that the price of a ticket was 5 dollars. Note that box office numbers divided by the ticket price gives you the number of visitors.

*** =instructions
	- Assign to `visitors` the matrix with the estimated number of Non-US and US visitors for the three movies.


*** =hint
The number of visitors is the revenue (which is stored in `star_wars_matrix` ) divided by the price of ticket (assumed to be $5).

*** =sample_code


```r
# Box office Star Wars: In Millions (!) 
# Construct matrix:
box_office_all 			= c(461, 314.4,290.5, 247.9,309.3,165.8)
movie_names    			= c("A new hope","The empire strikes back","Return of the Jedi")
col_titles     			= c("US","non-US")
star_wars_matrix  	= matrix(box_office_all, nrow=3, byrow=TRUE, dimnames=list(movie_names,col_titles))

# your code here!
visitors = 
```


*** =solution


```r
# Box office Star Wars: In Millions (!)  Construct matrix:
box_office_all = c(461, 314.4, 290.5, 247.9, 309.3, 165.8)
movie_names = c("A new hope", "The empire strikes back", "Return of the Jedi")
col_titles = c("US", "non-US")
star_wars_matrix = matrix(box_office_all, nrow = 3, byrow = TRUE, dimnames = list(movie_names, 
    col_titles))

# your code here!
visitors = star_wars_matrix/5
```


*** =sct


```r
if (!exists("star_wars_matrix")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'star_wars_matrix'.")
} else if (!isTRUE(try(all.equal(star_wars_matrix, matrix(box_office_all, nrow = 3, 
    byrow = TRUE, dimnames = list(movie_names, col_titles)))))) {
    DM.result = list(FALSE, "The 'star_wars_matrix' contains a wrong value.")
} else if (!exists("visitors")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'visitors'.")
} else if (!isTRUE(try(all.equal(visitors, star_wars_matrix/5)))) {
    DM.result = list(FALSE, "Looks like 'visitors' doesn't contain the correct value. Remember that operations on matrices are element-wise.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code




--- 

## A little arithmetic with matrices (2) 

Just like `2*my_matrix` multiplied every element of `my_matrix` by two, `my_matrix1 * my_matrix2` creates a matrix where each element is the product of the corresponding elements in `my_matrix1` and `my_matrix2`. 

After looking at the result of the previous exercise, big boss Lucas pointed out that the ticket prices went up over time with one dollar per movie. He asks to redo the analysis based on the prices you can find in `ticket_prices_matrix` (source: imagination). 

(Those familiar with matrices should note this is not the standard matrix multiplication for which you should use `%*%` in R.)

*** =instructions
	- Assign to `visitors` the matrix with your estimated number of Non-US and US visitors for the three movies.
	- Assign to `average_us_visitor` the average number of visitors in the US for a Star Wars movie.
	- Assign to `average_non_us_visitor` the average number of visitors in non-US areas.

*** =hint
	- You can use the function `mean()` to calculate the average of the inputs to the function.
	- To get the number of visitors in the US, select the first column from `visitors` using `visitors[ ,1]`.

*** =sample_code


```r
# Box office Star Wars: In Millions (!) 
# Construct matrix: 
box_office_all 				= c(461, 314.4,290.5, 247.9,309.3,165.8)
movie_names    				= c("A new hope","The empire strikes back","Return of the Jedi")
col_titles     				= c("US","non-US")
star_wars_matrix  		= matrix(box_office_all, nrow=3, byrow=TRUE, dimnames=list(movie_names,col_titles))
ticket_prices_matrix  = matrix(c(5,5,6,6,7,7), nrow=3, byrow=TRUE, dimnames=list(movie_names,col_titles)) 

# Your code below:
visitors = 
# Your code below:
average_us_visitor = 
# Your code below:
average_non_us_visitor =
```


*** =solution


```r
# Box office Star Wars: In Millions (!)  Construct matrix:
box_office_all = c(461, 314.4, 290.5, 247.9, 309.3, 165.8)
movie_names = c("A new hope", "The empire strikes back", "Return of the Jedi")
col_titles = c("US", "non-US")
star_wars_matrix = matrix(box_office_all, nrow = 3, byrow = TRUE, dimnames = list(movie_names, 
    col_titles))
ticket_prices_matrix = matrix(c(5, 5, 6, 6, 7, 7), nrow = 3, byrow = TRUE, dimnames = list(movie_names, 
    col_titles))

# Your code here
visitors = star_wars_matrix/ticket_prices_matrix
# Your code here
average_us_visitor = mean(visitors[, 1])
# Your code here
average_non_us_visitor = mean(visitors[, 2])
```


*** =sct


```r
if (!exists("star_wars_matrix")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'star_wars_matrix'.")
} else if (!isTRUE(try(all.equal(star_wars_matrix, matrix(box_office_all, nrow = 3, 
    byrow = TRUE, dimnames = list(movie_names, col_titles)))))) {
    DM.result = list(FALSE, "The 'star_wars_matrix' contains a wrong value.")
} else if (!exists("ticket_prices_matrix")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'ticket_prices_matrix'.")
} else if (!isTRUE(try(all.equal(ticket_prices_matrix, matrix(c(5, 5, 6, 6, 
    7, 7), nrow = 3, byrow = TRUE, dimnames = list(movie_names, col_titles)))))) {
    DM.result = list(FALSE, "The 'ticket_prices_matrix' contains a wrong value.")
} else if (!exists("visitors")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'visitors'.")
} else if (!isTRUE(try(all.equal(visitors, star_wars_matrix/ticket_prices_matrix)))) {
    DM.result = list(FALSE, "Looks like 'visitors' doesn't contain the correct value. Remember that you can divide two matrices.")
} else if (!exists("average_us_visitor")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'average_us_visitor'.")
} else if (!isTRUE(try(all.equal(average_us_visitor, mean(visitors[, 1]))))) {
    DM.result = list(FALSE, "Looks like 'average_us_visitor' doesn't contain the average of the US visitors.")
} else if (!exists("visitors")) {
    DM.result = list(FALSE, "Please make sure to define a variable 'visitors'.")
} else if (!isTRUE(try(all.equal(average_non_us_visitor, mean(visitors[, 2]))))) {
    DM.result = list(FALSE, "Looks like 'average_non_us_visitor' doesn't contain the average of the non-US visitors.")
} else {
    DM.result = list(TRUE, "Great! Continue to the next exercise.")
}
```


*** =pre_exercise_code



