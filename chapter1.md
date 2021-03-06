---
title       : Chapter 1
description : This is the first chapter.
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

---
## A really bad movie

```yaml
type: MultipleChoiceExercise
lang: r
xp: 50
skills: 1
key: cb75e904ce
```

Have a look at the plot that showed up in the viewer to the right. Which type of movie has the worst rating assigned to it?

`@instructions`
- Adventure
- Action
- Animation
- Comedy

`@hint`
Have a look at the plot. Which color does the point with the lowest rating have?

`@pre_exercise_code`
```{r}
# The pre exercise code runs code to initialize the user's workspace.
# You can use it to load packages, initialize datasets and draw a plot in the viewer

movies <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")

library(ggplot2)

ggplot(movies, aes(x = runtime, y = rating, col = genre)) + geom_point()
```

`@sct`
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "That is not correct!"
msg_success <- "Exactly! There seems to be a very bad action movie in the dataset."
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad))
```

---
## More movies

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: e013750490
```

In the previous exercise, you saw a dataset about movies. In this exercise, we'll have a look at yet another dataset about movies!

A dataset with a selection of movies, `movie_selection`, is available in the workspace.

`@instructions`
- Check out the structure of `movie_selection`.
- Select movies with a rating of 5 or higher. Assign the result to `good_movies`.
- Use `plot()` to  plot `good_movies$Run` on the x-axis, `good_movies$Rating` on the y-axis and set `col` to `good_movies$Genre`.

`@hint`
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`.

`@pre_exercise_code`
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code
load(url("https://s3.amazonaws.com/assets.datacamp.com/course/teach/movies.RData"))
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"), c("Genre", "Rating", "Run")]

# Clean up the environment
rm(Movies)
```

`@sample_code`
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection


# Select movies that have a rating of 5 or higher: good_movies


# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre

```

`@solution`
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

`@sct`
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

test_object("good_movies")

test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

test_error()

success_msg("Good work!")
```



---
## Bullet Exercise

```yaml
type: BulletExercise
key: 530e23fcbb
lang: r
xp: 100
```


`@pre_exercise_code`
```{r}

```


***

### Sub Exercise 1

```yaml
type: NormalExercise
xp: 100
key: 636ae50119
```

`@instructions`

This is the first sub-exercise 

`@sample_code`

```{r}
# Sample Code for Exercise 1
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```

***

### Sub Exercise 2

```yaml
type: NormalExercise
xp: 100
key: c721038005
```

`@instructions`

This is the second sub-exercise.


`@sample_code`

```{r}
# Sample Code for Exercise 2
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```

---
## Tab Exercise

```yaml
type: TabExercise
lang: r
xp: 100
key: 43b65f47bb
```

This is a Tab Exercise


`@pre_exercise_code`
```{r}

```


***

### Sub Exercise 1

```yaml
type: NormalExercise
xp: 100
key: f1c09bceac
```

`@instructions`

This is the first sub-exercise 

`@sample_code`

```{r}
# Sample Code for Exercise 1
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```

***

### Sub Exercise 2

```yaml
type: NormalExercise
xp: 100
key: a43e6c8fe1
```

`@instructions`

This is the second sub-exercise.


`@sample_code`

```{r}
# Sample Code for Exercise 2
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```



---
## Base Graphics vs. Ggplot2 (Part 1)

```yaml
type: TabExercise
key: a39aef6095
lang: r
xp: 100
```

To better appreciate `ggplot2` and understand how it works differently from base package, let us create a scatterplot of `hp` (horsepower) vs `drat` (rear axle ratio), colored by `cyl` (number of cylinders).

```{r}
# Base Graphics
plot(mtcars$hp, mtcars$drat, col = as.factor(mtcars$cyl))

# Ggplot2
ggplot(mtcars, aes(x = hp, y = drat, col = as.factor(cyl))) +
  geom_point()
```

Note that in both cases, we convert `cyl` to a factor as it represents discrete categories.


`@pre_exercise_code`
```{r}

```


***

### Sub Heading

```yaml
type: NormalExercise
xp: 100
key: fa5be44690
```

`@instructions`

Use base graphics to create a scatterplot of `mpg` vs `wt` colored by `gear` 


`@sample_code`
```{r}
# Create a scatterplot of `mpg` vs `wt` colored by `gear`
# Use base graphics
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```

***

### Sub Heading 2

```yaml
type: NormalExercise
xp: 100
key: 60a1c29d4f
```

`@instructions`

Use ggplot2 to create a scatterplot of `mpg` vs `wt` colored by `gear` 


`@sample_code`
```{r}
# Create a scatterplot of `mpg` vs `wt` colored by `gear` 
# Use ggplot2
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```



---
## Arithmetic with R

```yaml
type: BulletExercise
key: f7ada8b84e
lang: r
xp: 100
```

In its most basic form, R can be used as a simple calculator.

| Operation        | Symbol | Input    | Output |
|------------------|--------|----------|--------|
| Addition         |   +    | 5 + 2    |   7    |
| Subtraction      |   -    | 5 - 2    |   3    |
| Multiplication   |   *    | 5 * 2    |   10   |
| Division         |   /    | 5 / 2    |   2.5  |
| Integer Division |  %/%   | 5 %/% 2  |   2    |
| Modulo           |  %%    | 5 %% 2   |   1    |
| Exponentiation   |   ^    | 5^2      |   25   |
 

The last two might need some explaining:

- 5 modulo 2 returns the reminder of dividing 5 by 2 to give 1
- 5^2 raises 5 to the power of 2 to give 25


`@pre_exercise_code`
```{r}

```

***

### Sub Heading

```yaml
type: NormalExercise
xp: 100
key: 9e93e150fa
```

`@instructions`

Multiply the number 4 by 6

`@sample_code`
```{r}

```


`@hint`

`@solution`
```{r}

```

`@sct`
```{r}

```

***

### Sub Heading 2

```yaml
type: NormalExercise
xp: 100
key: 6d849a3a85
```

`@instructions`

Calculate 2 to the power of 5

`@sample_code`
```{r}

```


`@hint`

`@solution`
```{r}

```

`@sct`
```{r}

```

***

### Sub Heading 2

```yaml
type: NormalExercise
xp: 100
key: e864388921
```

`@instructions`

Compute the remainder of 28 divided by 6




`@hint`

`@solution`
```{r}

```

`@sct`
```{r}

```

---

## Positioning Bars

```yaml
type: BulletExercise
xp: 100
lang: r
key: b2778c38b2
```

While drawing a bar plot with multiple groups, you can position them using the `position` argument to [`geom_bar()`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_bar).

![image](https://imgur.com/RNWsjPJ.png)



<!--

In the previous chapter you saw that there are lots of ways to position scatter plots. Likewise, the [`geom_bar()`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_bar) and [`geom_histogram()`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_histogram) geoms also have a `position` argument, which you can use to specify how to draw the bars of the plot.

Three `position` arguments will be introduced here:

- `stack`: place the bars on top of each other. Counts are used. **This is the default position**.
- `fill`: place the bars on top of each other, but this time use proportions.
- `dodge`: place the bars next to each other. Counts are used.
-->

In this exercise you'll draw a bar plot of the count of cars by number of cylinders (`cyl`), according to manual or automatic transmission type (`am`) 

<!--
Since, in the built-in `mtcars` data set, `cyl` and `am` are integers, they have already been converted to factor variables for you.
-->

`@pre_exercise_code`

```{r eval = FALSE}
library(ggplot2)
mtcars$cyl <- factor(mtcars$cyl)
mtcars$am <- factor(mtcars$am)
# ggplot(mtcars, aes(x = cyl, fill = am)) +
#  geom_bar(position = "dodge")
```

***

```yaml
type: NormalExercise
xp: 25
key: 2c082a3672
```

`@instructions`

Use [`geom_bar()`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_bar) to make a bar plot of `cyl` filled by `am`.

`@hint`

Use [`aes()`](http://www.rdocumentation.org/packages/ggplot2/functions/aes) within [`ggplot()`](http://www.rdocumentation.org/packages/ggplot2/functions/ggplot) to map `x = cyl` and `fill = am`. You don't have to use [`factor()`](http://www.rdocumentation.org/packages/base/functions/factor) here, because these variables are already factors within the `mtcars` dataset. Add [`geom_bar()`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_bar) to the command.

`@sample_code`

```{r eval = FALSE}
# Draw a bar plot of cyl, filled by am, stacked on top of each other
ggplot(mtcars, aes(x = cyl, fill = am)) +
  ___()
```

`@solution`

```{r eval = FALSE}
# Draw a bar plot of cyl, filled according to am
ggplot(mtcars, aes(x = cyl, fill = am)) +
  geom_bar()
```

`@sct`

```{r}
test_ggplot()
```


***

```yaml
type: NormalExercise
xp: 25
key: 44fe7a3ff2
```

`@instructions`

Set `position` to "dodge" in [`geom_bar()`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_bar). 

`@hint`

Set  [`geom_bar(position = "dodge")`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_bar).

`@sample_code`

```{r eval = F}
# Draw a bar plot of cyl, filled by am, with position set to 'dodge'
ggplot(mtcars, aes(x = ___, fill = ___)) +
  ___(position = ___)
```

`@solution`

```{r}
# Draw a bar plot of cyl, filled by am, with position set to 'dodge'
ggplot(mtcars, aes(x = cyl, fill = am)) +
  geom_bar(position = "dodge")
```


`@sct`

```{r}
test_ggplot()
```

***

```yaml
type: NormalExercise
xp: 25
key: 6c8f23d7c3
```

`@instructions`

Set `position` to "fill" in [`geom_bar()`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_bar).

`@hint`

Set [`geom_bar(position = "fill")`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_bar).


`@sample_code`

```{r eval = F}
# Draw a bar plot of cyl, filled by am, with position set to 'fill'
ggplot(___, aes(x = ___, fill = ___)) +
  ___(___ = ___)
```

`@solution`

```{r}
# Draw a bar plot of cyl, filled by am, with position set to 'fill'
ggplot(mtcars, aes(x = cyl, fill = am)) +
  geom_bar(position = "fill")
```

`@sct`

```{r}
test_ggplot()
```

***

```yaml
type: NormalExercise
xp: 25
key: 466a608208
```

`@instructions`

Set `position` to "stack" in [`geom_bar()`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_bar).

`@hint`

Set [`geom_bar(position = "stack")`](http://www.rdocumentation.org/packages/ggplot2/functions/geom_bar).

`@sample_code`

```{r eval = F}
# Draw a bar plot of cyl, filled by am, with position set to 'stack'


```

`@solution`

```{r eval=FALSE}
# Draw a bar plot of cyl, filled by am, with position set to 'stack'
ggplot(mtcars, aes(x = cyl, fill = am)) +
  geom_bar(position = "dodge")
```

`@sct`

```{r}
test_ggplot()
success_msg("Good job! Different kinds of plots need different `position` arguments, so it's important to be familiar with this attribute.")
```



---

<style>
.note {
  background: #36D57D;
  padding: 10px;
  position: fixed;
  bottom: 5px;
  left: 5px;
  width: 100%;
  z-index: 999;
</style>

<div class="note">
This is an interactive coding exercise, where users write code in an editor and submit it.
</div>

## Normal Exercise

```yaml
type: NormalExercise
key: acb7e544ee
lang: r
xp: 100
skills: 1
```




`@instructions`

`@hint`

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}

```

`@solution`
```{r}

```

`@sct`
```{r}

```



---
## Bullet Exercise - Fading

<style>
.note {
  background: #36D57D;
  padding: 10px;
  position: fixed;
  bottom: 5px;
  left: 5px;
  width: 100%;
  z-index: 999;
</style>

<div class="note">
A BulletExercise can be used for fading!
</div>

```yaml
type: BulletExercise
key: 8aeaeeedb8
lang: r
xp: 100
```


`@pre_exercise_code`
```{r}

```


***

### Sub Heading

```yaml
type: NormalExercise
xp: 100
key: 9a11b6f49e
```

`@instructions`

Sub Exercise 1

`@sample_code`
```{r}
  
```

`@hint`

`@solution`
```{r}
x = 10
x
```

`@sct`
```{r}

```

***

### Sub Heading 2

```yaml
type: NormalExercise
xp: 100
key: ec7e0368bd
```
`@instructions`

Sub Exercise 2

`@sample_code`
```{r}
  
```

`@hint`

`@solution`
```{r}
x = 10
x
```

`@sct`
```{r}

```



---
## NormalExercise

```yaml
type: PureMultipleChoiceExercise
key: 7bf8572838
xp: 50
skills: 1
```

A `NormalExercise` gives students some background information and instructions, then checks the code they submit and provides feedback. The exercise and instructions are shown on the left, the code editor in the top right, and an interactive console for experimentation in the bottom right. Code is executed in two processes/environments so that you can safely compare objects in them in the submission correctness tests.

![normex](http://authoring.datacamp.com/images/NormalExercise.png)


`@possible_answers`

`@hint`

`@feedbacks`

