Activity 11: Statistical reasoning 3: multiple regression and DAGs
================

Welcome! This is the third statistical reasoning activity. The goals of
this activity are to understand how to implement DAGs in the context of
multiple regression.

------------------------------------------------------------------------

You will submit one output for this activity:

1.  A **PDF** of a rendered Quarto document with all of your R code.
    Please create a new Quarto document (e.g. don’t use this
    `README.qmd`), include all of the code that appears in this
    document, in addition to adding your own code and **answers to all
    of the questions** in the “Q#” sections. Submit this through
    Gradescope.

*If you have trouble submitting as a PDF, please ask Calvin or Malin for
help. If we still can’t solve it, you can submit the .qmd file instead.*

A reminder: **Please label the code** in your final submission in two
ways: 1) denote your answers to each question using headers that
correspond to the question you’re answering and 2) thoroughly “comment”
your code: remember, this means annotating your code directly by typing
descriptions of what each line does after a `#`. This will help future
you!

------------------------------------------------------------------------

Let’s start by reading in the relevant packages

``` r
# Run this to install some data packages
# devtools::install_github("rmcelreath/rethinking")
library(rethinking)

library(brms) # for statistics
library(tidyverse) # for data wrangling
# install.packages("dagitty_0.3-4.tgz", repos = NULL, type = "source")
# library("daggity")
```

# DAG practice

6M1. Modify the DAG on page 186 to include the variable V, an unobserved
cause of C and Y: C ← V → Y. Reanalyze the DAG. How many paths connect X
to Y? Which must be closed? Which variables should you condition on now?

------------------------------------------------------------------------

------------------------------------------------------------------------

# Foxes: Regression practice informed by DAGs

``` r
# Load in the fox data
data(foxes)

# Check out the fox data
?foxes
head(foxes)
```

      group avgfood groupsize area weight
    1     1    0.37         2 1.09   5.02
    2     1    0.37         2 1.09   2.84
    3     2    0.53         2 2.05   5.33
    4     2    0.53         2 2.05   6.07
    5     3    0.49         2 2.12   5.85
    6     3    0.49         2 2.12   3.25

“All three problems below are based on the same data. The data in
data(foxes) are 116 foxes from 30 different urban groups in England.
These foxes are like street gangs. Group size varies from 2 to 8
individuals. Each group maintains its own urban territory. Some
territories are larger than others. The area variable encodes this
information. Some territories also have more avgfood than others. We
want to model the weight of each fox. For the problems below, assume the
following DAG:”

![fox DAG](foxDAG.jpg)

------------------------------------------------------------------------

6H3. Use a model to infer the total causal influence of area on weight.
Would increasing the area available to each fox make it heavier
(healthier)? You might want to standardize the variables. Regardless,
use prior predictive simulation to show that your model’s prior
predictions stay within the possible outcome range.

------------------------------------------------------------------------

6H4. Now infer the causal impact of adding food to a territory. Would
this make foxes heavier? Which covariates do you need to adjust for to
estimate the total causal influence of food?

------------------------------------------------------------------------

6H5. Now infer the causal impact of group size. Which covariates do you
need to adjust for? Looking at the posterior distribution of the
resulting model, what do you think explains these data? That is, can you
explain the estimates for all three problems? How do they go together?

------------------------------------------------------------------------

------------------------------------------------------------------------

### Render to PDF

When you have finished, remember to pull, stage, commit, and push with
GitHub:

- Pull to check for updates to the remote branch
- Stage your edits (after saving your document!) by checking the
  documents you’d like to push
- Commit your changes with a commit message
- Push your changes to the remote branch

Then submit the well-labeled PDF on Gradescope. Thanks!
