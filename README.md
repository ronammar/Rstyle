# My R style guide

This style guide outlines how I like to code in [`R`](https://cran.r-project.org). I try to maintain R code etiquette based on the general R community's style. Like any style, it's evolving.

### File naming

Use the `.R` file extension, not lower case `.r`. When a file name is composed of multiple words, they should be seprated by underscores. I also avoid hyphens. Names should be descriptive, but there's no need to be too strict. Just *use good judgement*.

```bash
# Good:
fold_rna.R
getGeneExpression.R
detect.svm.R
# Bad:
my-program.r
perform_linear_regression_analysis_on_data.r
```

### Sources

I've stood on the shoulders of giants to learn my flavor of R style.

[The Google R Style Guide](https://google.github.io/styleguide/Rguide.xml)

[Hadley Wickham's Advanced R Style Guide](http://adv-r.had.co.nz/Style.html)
