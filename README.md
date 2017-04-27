
<!-- README.md is generated from README.Rmd. Please edit that file -->
splot - Stefan's plotting package
=================================

Just another [ggplot2](http://ggplot2.tidyverse.org) extension.

Installation
------------

Installation
------------

``` r
# Or the the development version from GitHub:
# install.packages("devtools")
devtools::install_github("stefanedwards/splot")
```

Usage
-----

We can display a limit on the axes range.

``` r
library(splot)
#> Loading required package: ggplot2
#> Loading required package: grid
#> Loading required package: gridExtra
#> Loading required package: gtable
ggplot(mtcars, aes(x=cyl, y=mpg)) + 
  geom_point() + 
  coord_capped_cart(bottom='both', left='none') +
  theme_light() + theme(panel.border=element_blank(), axis.line = element_line())
```

![](README-usage1-1.png)

**NB**: Disable `panel.border` and enable `axis.line` in `theme`, otherwise you will not see an effect!

We could also show that the x-axis is categorical (or ordinal):

``` r
ggplot(mtcars, aes(x=as.factor(cyl), y=mpg)) + 
  geom_point(position=position_jitter(width=0.1)) + 
  coord_flex_cart(bottom=brackets_horisontal(), left=capped_vertical('none')) +
  theme_light() + theme(panel.border=element_blank(), axis.line = element_line())
```

![](README-brackets_demo-1.png)
