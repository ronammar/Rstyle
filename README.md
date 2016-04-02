# My R style guide

This style guide outlines how I like to code in [`R`](https://cran.r-project.org). I try to maintain R code etiquette based on the general R community's style. Like any style, it's evolving.

**File naming:** Use the `.R` file extension, not lower case `.r`. When a file name is composed of multiple words, they should be seprated by underscores. I avoid hyphens. Names should be descriptive, but there's no need to be too strict. Just *use good judgement*. Examples: `fold_rna.R`, `getGeneExpression.R`, `detect.svm.R`.
If files need to be run in sequence, do not prefix them with numbers (eg. `0-getPlayers.R`, `1-computeScores.R`, `2-findMVP.R`). Instead, create a separate script that sources these programs and runs the code in sequence. It is more [*reproducible*](https://en.wikipedia.org/wiki/Reproducibility).

**Variable and function names:** I like to use [camelCase](https://en.wikipedia.org/wiki/CamelCase) with the first letter in lower case. Names composed of multiple words can also be delimited by underscores or periods. Examples: `df`, `carSafetyData`, `expression.norm`.

**Line length:** It's good practice not to exceed 80 characters. I think this is partly due to legacy terminal screen widths as well as page widths when printing code. However, modern computers have high resolution bright screens and do a [pretty good job anti-aliasing fonts when scaled down](http://hivelogic.com/articles/top-10-programming-fonts/). So, try to stick to 80 characters, but if a line or two of code are 100 characters long, that's acceptable. PS- these days my preferred font is [Droid Sans Mono](https://www.google.com/fonts/specimen/Droid+Sans+Mono).

### Sources

[*If I have seen further, it is by standing on the shoulders of giants*](https://en.wikipedia.org/wiki/Standing_on_the_shoulders_of_giants)

[The Google R Style Guide](https://google.github.io/styleguide/Rguide.xml)

[The *Advanced R* Style Guide](http://adv-r.had.co.nz/Style.html)
