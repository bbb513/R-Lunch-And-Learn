--- 
title_meta  : Chapter 7
title       : "Foundations for inference: Confidence intervals"
description : In this two part lab we will investigate sampling distributions and the Central Limit Theorem as well as confidence intervals. We will use housing data from Ames, Iowa (a small town in the US) in our exploration.
framework : datacamp
mode: selfcontained

---
## One sample from Ames, Iowa

Welcome to Part B! In this part, we'll translate that concept of reliability of mean estimates into something more tangible: **confidence intervals**.

If you have access to data on an entire population, say the size of every house in Ames, Iowa, it's straight forward to answer questions like, “How big is the typical house in Ames?” and “How much variation is there in sizes of houses?”. If you have access to only a sample of the population, as is often the case, the task becomes more complicated. 

What is your best guess for the typical size if you only know the sizes of several dozen houses? This sort of situation requires that you use your sample to make inference on what your population looks like.

In this second part of the lab we'll start with a simple random sample of size 60 from the population. Specifically, this is a simple random sample of size 60. Note that the data set has information on many housing variables, but for the first portion of the lab we'll focus on the size of the house, represented by the variable `Gr.Liv.Area`.

*** =instructions
  - Draw a sample of size 60 from `population`. Assign it to `samp`.
  - Calculate the mean of your sample. Assign it to `sample_mean`. 
  - Draw a histogram of the sample.

*** =hint

If you're not sure how to proceed, you should go back and review Part A before you continue here.

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
set.seed(12345)
```

*** =solution


```r
# The 'ames' data frame is already loaded into the workspace

# Take a sample of size 60 of the population:
population = ames$Gr.Liv.Area
samp = sample(population, 60)

# Calculate the mean:
sample_mean = mean(samp)

# Draw a histogram:
hist(samp)

```


*** =sample_code


```r
# The 'ames' data frame is already loaded into the workspace

# Take a sample of size 60 of the population:
population = ames$Gr.Liv.Area
samp = 

# Calculate the mean:
sample_mean = 

# Draw a histogram:

```


*** =sct


```r
if (!exists("ames")) {
    DM.result = list(FALSE, "Seems like the data was not loaded correctly. Use the function 'load' to load the data frame into the workspace.")
} else if (!exists("population") || !identical(population, ames$Gr.Liv.Area)) {
    DM.result = list(FALSE, "Did you change the 'population' object? It should be equal to the 'Gr.Liv.Are' variable of the 'ames' data frame.")
} else if (!exists("samp") || (length(samp) != 60) || !all(is.numeric(samp)) || 
    any(is.na(samp))) {
    DM.result = list(FALSE, "Seems like something's wrong with your sample.")
} else if (!exists("sample_mean") || !identical(sample_mean, mean(samp))) {
    DM.result = list(FALSE, "Did you calculate the mean of your sample?")
} else if (isTRUE(try(function_has_arguments("sample", c("x", "size"), c("population", 
    "60"), eval = c(TRUE, TRUE))) == 1) && isTRUE(try(function_has_arguments("hist", 
    "x", "samp", eval = TRUE)) == 1)) {
    DM.result = list(TRUE, "Very good! One of the most common ways to describe the typical or central value of a distribution is to use the mean.")
} else if (!student_typed("sample(")) {
    DM.result = list(FALSE, "Use the 'sample' function to take a sample!")
} else if (!student_typed("hist(")) {
    DM.result = list(FALSE, "Don't forget to draw a histogram of the sample!")
} else if (isTRUE(try(function_has_arguments("hist", "x", "sample_mean")) == 
    1)) {
    DM.result = list(FALSE, "Draw a histogram of your sample, not its mean!")
} else {
    DM.result = list(FALSE, "There seems to be something wrong with your solution, please try again...")
}
```


--- type:MultipleChoiceExercise
## Question 7

Your distribution should be similar to others' distributions who also collect random samples from this population, but it is likely not exactly the same since it's a random sample.

*** =instructions
  - TRUE
  - FALSE

*** =hint

Maybe you should read a bit more on [random sampling](http://en.wikipedia.org/wiki/Sampling_%28statistics%29).

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
```

*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (identical(DM.result, 1)) {
    DM.result = list(TRUE, "Correct!")
} else {
    DM.result = list(FALSE, "Incorrect, think again.")
}
```


---
## Confidence intervals

Now let's return for a moment to the question that first motivated this lab: based on this sample, what can we infer about the population? 
Based only on this single sample, the best estimate of the average living area of houses sold in Ames would be the **sample mean**, usually denoted as $\overline{x}$ (here we're calling it `sample_mean`).

That serves as a good point estimate but it would be useful to also communicate how uncertain we are of that estimate. This can be captured by using a **confidence interval**.

We can calculate a 95% confidence interval for a sample mean by adding and subtracting 1.96 standard errors to the point estimate.
`se = sd(samp)/sqrt(60)
lower = sample_mean - 1.96 * se
upper = sample_mean + 1.96 * se
c(lower, upper)`

It is an important inference that we make with this: even though we don't know what the full population looks like, we're *95% confident that the true average size of houses in Ames lies between the values `lower` and `upper`*.

*** =instructions
  - Calculate the 95% confidence interval as described above.

*** =hint

If you are unfamiliar with the confidence interval formula, we refer you to the [class lectures](https://www.coursera.org/TODO) on Coursera.

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
population = ames$Gr.Liv.Area
set.seed(12345)
samp = sample(population, 60)
sample_mean = mean(samp)
```

*** =solution


```r
# The 'ames' data frame is already loaded into the workspace

# Calculate the standard error:
se = sd(samp)/sqrt(60)

# Calculate the lower and upper bounds of your confidence interval and print
# them:
lower = sample_mean - 1.96 * se
upper = sample_mean + 1.96 * se
c(lower, upper)

```


*** =sample_code


```r
# The 'ames' data frame is already loaded into the workspace

# Calculate the standard error:
se = 

# Calculate the lower and upper bounds of your confidence interval and print them:
lower = 
upper = 

```


*** =sct


```r
if (!exists("ames")) {
    DM.result = list(FALSE, "Seems like the data was not loaded correctly. Use the function 'load' to load the data frame into the workspace.")
} else if (!exists("samp") || (length(samp) != 60) || !all(is.numeric(samp)) || 
    any(is.na(samp))) {
    DM.result = list(FALSE, "Seems like something's wrong with your sample `samp`.")
} else if (!exists("sample_mean") || !identical(sample_mean, mean(samp))) {
    DM.result = list(FALSE, "Did you change 'sample_mean'? It should be the mean of your sample.")
} else if (!exists("se") || !identical(se, sd(samp)/sqrt(60))) {
    DM.result = list(FALSE, "You have an error calculating your standard error 'se'.")
} else if (!exists("lower") || !identical(lower, sample_mean - 1.96 * se)) {
    DM.result = list(FALSE, "You have an error calculating your lower bound 'lower'.")
} else if (!exists("upper") || !identical(upper, sample_mean + 1.96 * se)) {
    DM.result = list(FALSE, "You have an error calculating your upper bound 'upper'.")
} else if (!output_contains("c(lower,upper)")) {
    DM.result = list(FALSE, "Don't forget to print the bounds!")
} else {
    DM.result = list(TRUE, "Great! There are a few conditions that need to be met for this interval to be valid. What are these conditions?")
}
```


--- type:MultipleChoiceExercise
## Question 8

For the confidence interval to be valid, the sample mean must be normally distributed and have standard error $s / \sqrt(n)$. Which of the following is **not** a condition needed for this to be true?

*** =instructions
  - The sample is random.
  - The sample size, 60, is less than 10% of all houses.
  - The sample distribution must be nearly normal.

*** =hint

Review the [class lectures](https://class.coursera.org/statistics-001/lecture) if you don't know this.

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
```

*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (identical(DM.result, 3)) {
    DM.result = list(TRUE, "Correct!")
} else if (identical(DM.result, 2)) {
    DM.result = list(FALSE, "Incorrect, while we want larger samples, we still don't want the sample to be too large compared to the population.")
} else {
    DM.result = list(FALSE, "Incorrect, think again.")
}
```


--- type:MultipleChoiceExercise
## Question 9

What does "95% confidence" mean?

*** =instructions
  - 95% of the time the true average area of houses in Ames, Iowa, will be in this interval.
  - 95% of random samples of size 60 will yield confidence intervals that contain the true average area of houses in Ames, Iowa.
  - 95% of the houses in Ames have an area in this interval.
  - 95% confident that the sample mean is in this interval.

*** =hint

Review the [class lectures](https://class.coursera.org/statistics-001/lecture) if you don't know this.

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
```

*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (identical(DM.result, 2)) {
    DM.result = list(TRUE, "Correct!")
} else if (identical(DM.result, 1)) {
    DM.result = list(FALSE, "Incorrect, the population doesn't move from time to time.")
} else if (identical(DM.result, 3)) {
    DM.result = list(FALSE, "Incorrect, the confidence interval is about the population mean, not the individual sizes of houses.")
} else if (identical(DM.result, 4)) {
    DM.result = list(FALSE, "Incorrect, the sample mean will always be in the interval.")
} else {
    DM.result = list(FALSE, "Incorrect, think again.")
}
```


--- type:MultipleChoiceExercise
## Question 10

In this case you have the luxury of knowing the true population mean since we have data on the entire population. This value can be calculated using the following command: `mean(population)`.

*Tip: Check if your confidence interval `c(lower, upper)` captures the true average size of houses in Ames!*

**What proportion of 95% confidence intervals would you expect to capture the true population mean?**

*** =instructions
  - 1%
  - 5%
  - 99%
  - 95%

*** =hint

This is basically the definition of a confidence interval. If you don't know this, you should review the [class lectures](https://www.coursera.org/TODO). 

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
population = ames$Gr.Liv.Area
set.seed(12345)
samp = sample(population, 60)
sample_mean = mean(samp)
se = sd(samp)/sqrt(60)
lower = sample_mean - 1.96 * se
upper = sample_mean + 1.96 * se
```

*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (identical(DM.result, 4)) {
    DM.result = list(TRUE, "Correct!")
} else {
    DM.result = list(FALSE, "Incorrect, please review the definition of the confidence level.")
}
```


---
## Challenge (1)

To learn a bit more about how sample means and confidence intervals vary from one sample to another: **a challenge!**

Using R, we're going to recreate many samples using a for loop. Here is the rough outline:
  1. Obtain a random sample.
  2. Calculate the sample's mean and standard deviation.
  3. Use these statistics to calculate a confidence interval.
  4. Repeat steps (1)-(3) 50 times.

But let's start slowly by initializing the objects you'll use to store the means and standard deviations. We'll also store the desired sample size as `n`.

*** =instructions
  - Initialize `samp_mean` and `samp_sd` with 50 `NA` values. (Use the `rep` function.)
  - Set `n` to 60.

*** =hint

The `rep(x, times)` function replicates a given `x` for `times` amount of times. So a vector of 10 `NA` values would be `rep(NA, 10)`. 

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
```

*** =solution


```r
# The 'ames' data frame is already loaded into the workspace

# Initialize 'samp_mean', 'samp_sd' and 'n':
samp_mean = rep(NA, 50)
samp_sd = rep(NA, 50)
n = 60

```


*** =sample_code


```r
# The 'ames' data frame is already loaded into the workspace

# Initialize 'samp_mean', 'samp_sd' and 'n':
samp_mean = 
samp_sd = 
n = 

```


*** =sct


```r
if (!exists("ames")) {
    DM.result = list(FALSE, "Seems like the data was not loaded correctly. Use the function 'load' to load the data frame into the workspace.")
} else if (!exists("samp_mean") || !identical(samp_mean, rep(NA, 50))) {
    DM.result = list(FALSE, "Did you correctly initialize 'samp_mean'?")
} else if (!exists("samp_sd") || !identical(samp_sd, rep(NA, 50))) {
    DM.result = list(FALSE, "Did you correctly initialize 'samp_sd'?")
} else if (!exists("n") || !identical(n, 60)) {
    DM.result = list(FALSE, "Did you correctly initialize 'n'?")
} else {
    DM.result = list(TRUE, "Good! Now let's do the for loop.")
}
```


---
## Challenge (2)

Okay, remember the outline:
  1. Obtain a random sample.
  2. Calculate the sample's mean and standard deviation.
  3. Use these statistics to calculate a confidence interval.
  4. Repeat steps (1)-(3) 50 times.

Now that we've initialized our objects, we can use a **for loop** to calculate 50 times the mean and standard deviation of random samples.

In this exercise we're taking away the training wheels, so it will be a bit harder than the previous ones. But hey, that's why it's called a challenge!

*** =instructions
  - Use a for loop to do 50 times the following: (1) create a sample of size `n` from the `population` (call this `samp`). (2) Calculate the `mean` and `sd` and assign them to their correct positions in `samp_mean` and `samp_sd` depending on which iteration you're on.

*** =hint

As a reminder, the syntax of a for loop: `for (i in 1:n) { ... }`.

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
population = ames$Gr.Liv.Area
set.seed(12345)
```

*** =solution


```r
# The 'ames' data frame is already loaded into the workspace

# Initialize 'samp_mean', 'samp_sd' and 'n':
samp_mean = rep(NA, 50)
samp_sd = rep(NA, 50)
n = 60

# For loop goes here:
for (i in 1:50) {
    # Obtain a sample of size n = 60 from the population
    samp = sample(population, n)
    # Save sample mean in ith element of samp_mean
    samp_mean[i] = mean(samp)
    # Save sample sd in ith element of samp_sd
    samp_sd[i] = sd(samp)
}

```


*** =sample_code


```r
# The 'ames' data frame is already loaded into the workspace

# Initialize 'samp_mean', 'samp_sd' and 'n':
samp_mean = rep(NA, 50)
samp_sd = rep(NA, 50)
n = 60

# For loop goes here:

```


*** =sct


```r
if (!exists("ames")) {
    DM.result = list(FALSE, "Seems like the data was not loaded correctly. Use the function 'load' to load the data frame into the workspace.")
} else if (!exists("samp_mean") || identical(samp_mean, rep(NA, 50))) {
    DM.result = list(FALSE, "Did you assign anything to 'samp_mean'?")
} else if (!exists("samp_sd") || identical(samp_sd, rep(NA, 50))) {
    DM.result = list(FALSE, "Did you assign anything to 'samp_sd'?")
} else if (!exists("n") || !identical(n, 60)) {
    DM.result = list(FALSE, "Did you correctly set 'n' to 60?")
} else if (!exists("samp_mean") || (length(samp_mean) != 50) || !all(is.numeric(samp_mean)) || 
    any(is.na(samp_mean))) {
    DM.result = list(FALSE, "Seems like something's wrong with 'samp_mean'.")
} else if (!exists("samp_sd") || (length(samp_sd) != 50) || !all(is.numeric(samp_sd)) || 
    any(is.na(samp_sd))) {
    DM.result = list(FALSE, "Seems like something's wrong with 'samp_sd'.")
} else if (!exists("samp")) {
    DM.result = list(FALSE, "You should assign your random samples to 'samp'.")
} else if (isTRUE(try(function_has_arguments("sample", c("x", "size"), c("population", 
    "n"), eval = c(TRUE, TRUE))) == 1) && identical(samp_mean[50], mean(samp)) && 
    identical(samp_sd[50], sd(samp))) {
    DM.result = list(TRUE, "Very nice! That was tricky but you handled it very well.")
} else if (isTRUE(try(function_has_arguments("sample", c("x", "size"), c("population", 
    "n"), eval = c(TRUE, TRUE))) >= 2)) {
    DM.result = list(FALSE, "Almost, but you should calculate the mean and standard deviation from the same random sample in each iteration. Maybe assign the sample to a temporary object such as 'samp'?")
} else if (!isTRUE(try(function_has_arguments("sample", c("x", "size"), c("population", 
    "n"), eval = c(TRUE, TRUE))) == 1)) {
    DM.result = list(FALSE, "Did you take any random samples?")
} else {
    DM.result = list(FALSE, "Seems like something's wrong with your solution...")
}
```


---
## Challenge (3)

Lastly, we can construct the confidence intervals and plot them. In this exercise, you will have to calculate the 95% confidence intervals. 

If you don't remember, here is the formula for the lower and upper bound respectively:

$\overline{x} - 1.96 \times \frac{\sigma}{\sqrt(n)}$

$\overline{x} + 1.96 \times \frac{\sigma}{\sqrt(n)}$

You can use this formula to calculate the lower and upper bounds with just two lines. 

As a hint: `samp_mean * 2` in R will multiply all 50 of the means with 2.

*** =instructions
  - Calculate `lower` and `upper` bounds using the formula described above.
  - Inspect the plot that was generated with the provided custom function `plot_ci`.

*** =hint

$\overline{x}$ is the `samp_mean` and $\sigma$ is `samp_sd`.

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
population = ames$Gr.Liv.Area
set.seed(12345)
```

*** =solution


```r
# The 'ames' data frame is already loaded into the workspace

# Initialize 'samp_mean', 'samp_sd' and 'n':
samp_mean = rep(NA, 50)
samp_sd = rep(NA, 50)
n = 60

# For loop goes here:
for (i in 1:50) {
    samp = sample(population, n)
    samp_mean[i] = mean(samp)
    samp_sd[i] = sd(samp)
}

# Calculate the interval bounds here:
lower = samp_mean - 1.96 * (samp_sd/sqrt(n))
upper = samp_mean + 1.96 * (samp_sd/sqrt(n))

# Plotting the confidence intervals:
pop_mean = mean(population)
plot_ci(lower, upper, pop_mean)

```


*** =sample_code


```r
# The 'ames' data frame is already loaded into the workspace

# Initialize 'samp_mean', 'samp_sd' and 'n':
samp_mean = rep(NA, 50)
samp_sd = rep(NA, 50)
n = 60

# For loop goes here:
for (i in 1:50) {
    samp = sample(population, n)
    samp_mean[i] = mean(samp)
    samp_sd[i] = sd(samp)
}

# Calculate the interval bounds here:
lower = 
upper = 
# Plotting the confidence intervals:
pop_mean = mean(population)
plot_ci(lower, upper, pop_mean)

```


*** =sct


```r
if (!exists("ames")) {
    DM.result = list(FALSE, "Seems like the data was not loaded correctly. Use the function 'load' to load the data frame into the workspace.")
} else if (!exists("samp_mean") || identical(samp_mean, rep(NA, 50))) {
    DM.result = list(FALSE, "Did you assign anything to 'samp_mean'?")
} else if (!exists("samp_sd") || identical(samp_sd, rep(NA, 50))) {
    DM.result = list(FALSE, "Did you assign anything to 'samp_sd'?")
} else if (!exists("n") || !identical(n, 60)) {
    DM.result = list(FALSE, "Did you correctly set 'n' to 60?")
} else if (!exists("samp_mean") || (length(samp_mean) != 50) || !all(is.numeric(samp_mean)) || 
    any(is.na(samp_mean))) {
    DM.result = list(FALSE, "Seems like something's wrong with 'samp_mean'.")
} else if (!exists("samp_sd") || (length(samp_sd) != 50) || !all(is.numeric(samp_sd)) || 
    any(is.na(samp_sd))) {
    DM.result = list(FALSE, "Seems like something's wrong with 'samp_sd'.")
} else if (!exists("samp") || !isTRUE(try(function_has_arguments("sample", c("x", 
    "size"), c("population", "n"), eval = c(TRUE, TRUE))) == 1) || !identical(samp_mean[50], 
    mean(samp)) || !identical(samp_sd[50], sd(samp))) {
    DM.result = list(FALSE, "Did you change something to the for loop?")
} else if (!exists("lower") || !exists("upper")) {
    DM.result = list(FALSE, "Did you correctly define the lower and upper bouds of the interval?")
} else if (!exists("pop_mean") || !isTRUE(try(function_has_arguments("plot_ci", 
    c("lo", "hi", "m"), c("lower", "upper", "pop_mean"), eval = c(TRUE, TRUE, 
        TRUE))) == 1)) {
    DM.result = list(FALSE, "Did you change something to the code for the plot?")
} else if (identical(round(lower), round(samp_mean - 1.96 * samp_sd/sqrt(n))) && 
    identical(round(upper), round(samp_mean + 1.96 * samp_sd/sqrt(n)))) {
    DM.result = list(TRUE, "Perfecto!")
} else {
    DM.result = list(FALSE, "Seems like something's wrong with your solution, please try again.")
}
```


--- type:MultipleChoiceExercise
## Question 11

What is the appropriate critical value for a 99% confidence level?

*** =instructions
  - 0.01
  - 0.99
  - 1.96
  - 2.33
  - 2.58

*** =hint

The critical value for the 99% confidence level is the cut-off for the middle 99% of the standard normal distribution. You can use the command `qnorm(0.995)` or refer to a [table](http://www.openintro.org/stat/down/probTables.pdf).

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
```

*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (identical(DM.result, 5)) {
    DM.result = list(TRUE, "Correct!")
} else {
    DM.result = list(FALSE, "Incorrect, think again.")
}
```


---
## The 99%

Calculate 50 confidence intervals at the 99% confidence level. You do not need to obtain new samples, simply calculate new intervals based on the sample means and standard deviations you have already collected. Using the `plot_ci` function, plot all intervals and calculate the proportion of intervals that include the true population mean.

*** =instructions
  - Calculate `lower` and `upper` bounds using the formula described above.
  - Inspect the plot that was generated with the provided custom function `plot_ci`.

*** =hint

$\overline{x}$ is the `samp_mean` and $\sigma$ is `samp_sd`.

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
population = ames$Gr.Liv.Area
set.seed(12345)
```

*** =solution


```r
# The 'ames' data frame is already loaded into the workspace

# Initialize 'samp_mean', 'samp_sd' and 'n':
samp_mean = rep(NA, 50)
samp_sd = rep(NA, 50)
n = 60

# For loop goes here:
for (i in 1:50) {
    samp = sample(population, n)
    samp_mean[i] = mean(samp)
    samp_sd[i] = sd(samp)
}

# Calculate the interval bounds here:
lower = samp_mean - 2.58 * (samp_sd/sqrt(n))
upper = samp_mean + 2.58 * (samp_sd/sqrt(n))

# Plotting the confidence intervals:
pop_mean = mean(population)
plot_ci(lower, upper, pop_mean)

```


*** =sample_code


```r
# The 'ames' data frame is already loaded into the workspace

# Initialize 'samp_mean', 'samp_sd' and 'n':



# For loop goes here:





# Calculate the interval bounds here:



# Plotting the confidence intervals:

```


*** =sct


```r
if (!exists("ames")) {
    DM.result = list(FALSE, "Seems like the data was not loaded correctly. Use the function 'load' to load the data frame into the workspace.")
} else if (!exists("samp_mean") || identical(samp_mean, rep(NA, 50))) {
    DM.result = list(FALSE, "Did you assign anything to 'samp_mean'?")
} else if (!exists("samp_sd") || identical(samp_sd, rep(NA, 50))) {
    DM.result = list(FALSE, "Did you assign anything to 'samp_sd'?")
} else if (!exists("n") || !identical(n, 60)) {
    DM.result = list(FALSE, "Did you correctly set 'n' to 60?")
} else if (!exists("samp_mean") || (length(samp_mean) != 50) || !all(is.numeric(samp_mean)) || 
    any(is.na(samp_mean))) {
    DM.result = list(FALSE, "Seems like something's wrong with 'samp_mean'.")
} else if (!exists("samp_sd") || (length(samp_sd) != 50) || !all(is.numeric(samp_sd)) || 
    any(is.na(samp_sd))) {
    DM.result = list(FALSE, "Seems like something's wrong with 'samp_sd'.")
} else if (!exists("samp") || !isTRUE(try(function_has_arguments("sample", c("x", 
    "size"), c("population", "n"), eval = c(TRUE, TRUE))) == 1) || !identical(samp_mean[50], 
    mean(samp)) || !identical(samp_sd[50], sd(samp))) {
    DM.result = list(FALSE, "Did you change something to the for loop?")
} else if (!exists("lower") || !exists("upper")) {
    DM.result = list(FALSE, "Did you correctly define the lower and upper bouds of the interval?")
} else if (!exists("pop_mean") || !isTRUE(try(function_has_arguments("plot_ci", 
    c("lo", "hi", "m"), c("lower", "upper", "pop_mean"), eval = c(TRUE, TRUE, 
        TRUE))) == 1)) {
    DM.result = list(FALSE, "Did you change something to the code for the plot?")
} else if (identical(round(lower), round(samp_mean - 2.58 * samp_sd/sqrt(n))) && 
    identical(round(upper), round(samp_mean + 2.58 * samp_sd/sqrt(n)))) {
    DM.result = list(TRUE, "Correct!")
} else {
    DM.result = list(FALSE, "Seems like something's wrong with your solution, please try again.")
}
```


--- type:MultipleChoiceExercise contains_graph:TRUE
## Question 12

We would expect 99% of the intervals to contain the true population mean.

*** =instructions
  - TRUE
  - FALSE

*** =hint

Think about the definition of the confidence level.

*** =pre_exercise_code


```r
load(url("http://s3.amazonaws.com/assets.datacamp.com/course/dasi/ames.RData"))
population = ames$Gr.Liv.Area
set.seed(12345)
samp_mean = rep(NA, 50)
samp_sd = rep(NA, 50)
n = 60
for (i in 1:50) {
    samp = sample(population, n)
    samp_mean[i] = mean(samp)
    samp_sd[i] = sd(samp)
}
lower = samp_mean - 2.58 * (samp_sd/sqrt(n))
upper = samp_mean + 2.58 * (samp_sd/sqrt(n))
pop_mean = mean(population)
plot_ci(lower, upper, pop_mean)
```

*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (identical(DM.result, 1)) {
    DM.result = list(TRUE, "Correct! It's been quite a long journey but you've made it through lab 3, congratulations!")
} else {
    DM.result = list(FALSE, "Incorrect, think again.")
}
```


--- type:MultipleChoiceExercise
## End of Lab Survey - Question 1

At the end of every lab, you will be asked to take a short survey existing out of 5 questions. These questions are not graded, but your feedback is very much appreciated and immensely useful for the development of the course.  Let's start with question one:

This lab covered material that is covered in the class.

*** =instructions
- Strongly Disagree
- Disagree
- Neutral
- Agree
- Strongly Agree

*** =hint

Just give us your honest opinion ;-) 

*** =pre_exercise_code



*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (DM.result %in% c(1:5)) {
    DM.result = list(TRUE, "One down, four to go!")
} else {
    DM.result = list(FALSE, "Please select one of the options!")
}
```


--- type:MultipleChoiceExercise
## End of Lab Survey - Question 2

The lab improved my understanding of these topics.

*** =instructions
- Strongly Disagree
- Disagree
- Neutral
- Agree
- Strongly Agree

*** =hint

Just give us your honest opinion ;-) 

*** =pre_exercise_code



*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (DM.result %in% c(1:5)) {
    DM.result = list(TRUE, "Let's look at the next one!")
} else {
    DM.result = list(FALSE, "Please select one of the options!")
}
```


--- type:MultipleChoiceExercise
## End of Lab Survey - Question 3

The instructions were clear and it was easy to understand what was wanted.

*** =instructions
- Strongly Disagree
- Disagree
- Neutral
- Agree
- Strongly Agree

*** =hint

Just give us your honest opinion ;-) 

*** =pre_exercise_code



*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (DM.result %in% c(1:5)) {
    DM.result = list(TRUE, "Click next for the fourth survey question")
} else {
    DM.result = list(FALSE, "Please select one of the options!")
}
```



--- type:MultipleChoiceExercise
## End of Lab Survey - Question 4

The data were relevant and interesting to me.

*** =instructions
- Strongly Disagree
- Disagree
- Neutral
- Agree
- Strongly Agree

*** =hint

Just give us your honest opinion ;-) 

*** =pre_exercise_code



*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (DM.result %in% c(1:5)) {
    DM.result = list(TRUE, "Up to the final question!")
} else {
    DM.result = list(FALSE, "Please select one of the options!")
}
```



--- type:MultipleChoiceExercise
## End of Lab Survey - Question 5

The length of time took to complete lab.

*** =instructions
- Less than 30 minutes
- Between 30 minutes and 1 hour
- Between 1 hour and 2 hours
- More than 2 hours

*** =hint

Just give us your honest opinion ;-) 

*** =pre_exercise_code



*** =solution




*** =sample_code




*** =sct


```r
if (!exists("DM.result")) {
    DM.result = list(FALSE, "Please select one of the options!")
} else if (DM.result %in% c(1:4)) {
    DM.result = list(TRUE, "A big THANKS for your feedback! See you next week.")
} else {
    DM.result = list(FALSE, "Please select one of the options!")
}
```

