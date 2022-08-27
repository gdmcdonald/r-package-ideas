# r-package-ideas
Things that should be, but aRen't (yet).

# [`notly`](https://github.com/gdmcdonald/notly)

~~Notly would have a single function, `notly::notly()` which is basically the inverse function to `plotly::ggplotly()`, i.e. it turns a plotly plot back into a ggplot object.~~

~~This way if you've saved an interactive plotly object you can recover the ggplot from it!~~

~~Probably this would be hard to do unless - you overwrote the ggplotly function with `notly::ggplotly()` to also save the ggplot object. That way it can simply be extracted and not reverse engineered.~~

edit: [done!](https://github.com/gdmcdonald/notly)

# `git-shame`

Git shame will to a simmilarity search on your code, and match lines of code with stack overflow answers if they are above a certain threshold. It can then (optionally) add a comment in the code to indicate where you shamelessly stole it from.

# `faker`

Faker would either invent a fake data set from scratch with certain configurable parameters, or copy an existing dataset's structure but replacing the values.

This would be useful, for example, when the poriginal dataset is not allowed to be shared, e.g. private medical records could have the names and values replaced so that someone else could prototype a model/some code with the correct structure of the data, when they don't have access to the confidential data itself.

Further improvements could be to try to match the statistical distribution of the fake replacement data to the original data under certain assumptions.

# `namer`

Generates good names for R packages and functions by finding memorable short words that aren't taken already on CRAN or as functions in popular packages, using thesaurus/dictionary or adding in the letter R in the package name the way people seem to do.

# `jsmodel`

Exports a model (e.g. a regression or classification from tidymodels) into a JavaScript widget so that you can put it on a website and predict live in a user's browser. 

How to implement this? Maybe to start it's easiest to train the model in tidymodels using a tensorflow engine, then convert that to js? But that doesn't sound very lightweight.

# `once`

Wraps an expensive operation so that output is saved to disk. If the file exists, it won't run again, it will just load the saved version. 

Eg. instead of 

```{r}
model_file <- "saved_models/my_trained_models.Rds"

if (file.exists(model_file)){
  my_trained_models <- readRDS(file = model_file)
} else {
  # Train all the models 
  my_trained_models <- train_models_function(...)
  saveRDS(my_trained_models, file = model_file)
}
```

it would look like

```{r}
  my_trained_models <- 
    train_models_function(...) %>%
    once(model_file = "saved_models/my_trained_models.Rds")
```

# `corgui`

It's an interactive correlation plot (correlation /mutual information / ...), that you can click on a square (any combination of parameters) to get a zoom in which is a scatterplot with a linear trend / cubic spline / rf regression. And yes, it's pronounced "Corgi".


