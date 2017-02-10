# My R style guide

> **A basic structural design underlies every kind of writing.**

> -Strunk & White in *The Elements of Style*

This style guide outlines how I like to code in [`R`](https://cran.r-project.org). I try to maintain R code etiquette based on the general R community's style. Like any style, it's evolving.

If you want to quickly learn my style, I've distilled my general rules into one liners for each section.

**File naming:** Use the `.R` file extension, not lower case `.r`.

When a file name is composed of multiple words, they should be seprated by underscores. I avoid hyphens. Names should be descriptive, but there's no need to be too strict. Just *use good judgement*. Examples: `fold_rna.R`, `getGeneExpression.R`, `detect.svm.R`.
If files need to be run in sequence, do not prefix them with numbers (eg. `0-getPlayers.R`, `1-computeScores.R`, `2-findMVP.R`). Instead, create a separate script that sources these programs and runs the code in sequence. It is more [*reproducible*](https://en.wikipedia.org/wiki/Reproducibility).

**Variable and function names:** Use [camelCase](https://en.wikipedia.org/wiki/CamelCase) with the first letter in lower case.

Names composed of multiple words can also be delimited by underscores or periods. Examples: `df`, `carSafetyData`, `expression.norm`, `top_acceleration_list`. Just don't mix styles like this `top_Acceleration.list`. I try to avoid using upper case for the first character in variable or function names because, in my experience, this leads to typos. An example of this would be the `View()` function in R. Often when I'm typing quickly, I will mistype it as `view()` or `vIew()`.

**Line length:** It's good practice not to exceed 80 characters.

I think this is partly due to legacy terminal screen widths as well as page widths when printing code. However, modern computers have high resolution bright screens and do a [pretty good job anti-aliasing fonts when scaled down](http://hivelogic.com/articles/top-10-programming-fonts/). And printing code is often a waste of paper. So, try to stick to 80 characters, but if a line or two of code are 100 characters long, that's acceptable. *PS- these days my preferred font is [Droid Sans Mono](https://www.google.com/fonts/specimen/Droid+Sans+Mono).*

**Indentation:** Use 2 spaces to indent a code block. Don't use tabs.

Many text editors allow you to record 2 spaces when you type a tab instead of the [ASCII](https://en.wikipedia.org/wiki/ASCII) horizontal tab `\t` character. You may also choose 4 or some other number of spaces. Make sure this behavior is enabled. Any programmer of [Python](https://www.python.org), a language where execution is predicated on indentation, surely knows the [fun](http://stackoverflow.com/questions/120926/why-does-python-pep-8-strongly-recommend-spaces-over-tabs-for-indentation) of mixing tabs with spaces which are almost always visually indistinguishable in a text editor. Stick with 2 spaces - it'll save you time one day.

**Assignment:** Use `<-` not `=`.

Note, the `<-` operator looks like a left-pointing arrow (:arrow_left:). There are cases where `<-` and `=` will not have the same behavior, in particular when `<-` is intended. For example:

```r
quote(y <- 5)
# y <- 5
quote(y = 5)
# Error in quote(y = 5) : supplied argument name 'y' does not match 'expr'
```

This is explained nicely [here](https://ironholds.org/projects/rbitrary/#okay.-and-should-we-be-using---or-people-keep-telling-me-to-use--.).

[Rick Becker](http://www.research.att.com/people/Becker_Richard_A), the co-creator of [S](https://en.wikipedia.org/wiki/S_(programming_language)) (R's predecessor), explained the rationale for using the `<-` operator at the R user conference [*useR 2016*](http://user2016.org). On the TTY37 keyboard, the keyboards connected to the [Bell Labs PDP-11](https://commons.wikimedia.org/wiki/File:Ken_Thompson_(sitting)_and_Dennis_Ritchie_at_PDP-11_(2876612463).jpg), the operator was input via a single key press:

![](images/why_arrow_operator.jpg)

**Spacing:** Add spaces around binary operators (`=`, `+`, `-`, `<-`, etc.). Add spaces after a comma, but not before. Exceptions are for operators `:`, `::`, `:::`, which are not flanked by spaces. Also, when using `=` in a function call, do not flank the operator by spaces.

```r
# Stylish
numbers <- 1:100 * 2
random <- rnorm(25, mean=5)
paste("meta", "analysis", sep="-")
mtcars[1, ]
# Drab
numbers=1 : 100*2  # note that this is equivalent to the stylish numbers
random <- rnorm( 25 , mean = 5)
random<-rnorm(25,mean=5)
mtcars[1,]
```

Place a space before left round bracket `(`, except in a function call. 

```r
# Stylish
for (l in letters) print(l)
rnorm(100)
# Drab
for(l in letters) print (l)
rnorm (100)
```

I prefer not to line up assignment operators. This can get messy and the spacing rules become dependent on the next variable name which may not exist yet.

```r
# 7:26am
a <- 1
# 7:31am
a    <- 1
cars <- rownames(mtcars)
# 7:45am
a            <- 1
cars         <- rownames(mtcars)
displacement <- mtcars$disp
# 8:00am and an unfortunate variable name
a                                              <- 1
cars                                           <- rownames(mtcars)
displacement                                   <- mtcars$disp
regression_model_displacement_miles_per_gallon <- lm(disp ~ mpg, mtcars)
# 8:20am refactoring, changing the name and updating all assignments again
a             <- 1
cars          <- rownames(mtcars)
displacement  <- mtcars$disp
regr_disp_mpg <- lm(disp ~ mpg, mtcars)
```

But you should line up parameters in a function call:

```r

```

TODO:
- R function calls and partial, ordered matching of arguments
- lazy eval and arguments within arguments
- importance of using the pipe `%>%`; give example of passing arguments
- if you have to copy a chunk of code at least once (such that it appears at least twice), time to write a function
  - old saying: if code chunk is duplicated, it'll be wrong at least once
- `library` vs `require`
- function naming and the `.` character; see advanced R page 103
- Add template for R scripts - best practices (`set.seed()`, `rm(list=ls())`, etc)
- incorporate ideas from tidy tools [manifesto](https://cran.r-project.org/web/packages/tidyverse/vignettes/manifesto.html)
- Load `.RData` objects into "sandboxed" environments so as not to pollute your local namespace

### Sources

[*If I have seen further, it is by standing on the shoulders of giants*](https://en.wikipedia.org/wiki/Standing_on_the_shoulders_of_giants):

* [The Google R Style Guide](https://google.github.io/styleguide/Rguide.xml)
* [The *Advanced R* Style Guide](http://adv-r.had.co.nz/Style.html)
