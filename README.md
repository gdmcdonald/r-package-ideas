# r-package-ideas
Things that should be, but aRen't (yet).

# [`notly`](https://github.com/gdmcdonald/notly)

~~Notly would have a single function, `notly::notly()` which is basically the inverse function to `plotly::ggplotly()`, i.e. it turns a plotly plot back into a ggplot object.~~

~~This way if you've saved an interactive plotly object you can recover the ggplot from it!~~

~~Probably this would be hard to do unless - you overwrote the ggplotly function with `notly::ggplotly()` to also save the ggplot object. That way it can simply be extracted and not reverse engineered.~~

edit: [done!](https://github.com/gdmcdonald/notly)

<img width="210" alt="Notly" src="https://user-images.githubusercontent.com/20785842/187099756-63951a1a-45d4-4903-8acb-b86c54764564.png">

# `git-shame`

Git shame will to a simmilarity search on your code, and match lines of code with stack overflow answers if they are above a certain threshold. It can then (optionally) add a comment in the code to indicate where you shamelessly stole it from.

# `faker`

Faker would either invent a fake data set from scratch with certain configurable parameters, or copy an existing dataset's structure but replacing the values.

This would be useful, for example, when the original dataset is not allowed to be shared, e.g. private medical records could have the names and values replaced so that someone else could prototype a model/some code with the correct structure of the data, when they don't have access to the confidential data itself.

Further improvements could be to try to match the statistical distribution of the fake replacement data to the original data under certain assumptions.

<img width="344" alt="faker" src="https://user-images.githubusercontent.com/20785842/187031917-099efb71-98e4-4649-948b-6c18654deb2e.png">

# `namer`

Generates good names for R packages and functions by finding memorable short words that aren't taken already on CRAN or as functions in popular packages, using thesaurus/dictionary or adding in the letter R in the package name the way people seem to do.

<img width="342" alt="namer" src="https://user-images.githubusercontent.com/20785842/187032082-ed219acf-bcf3-41cb-a316-9af4d45db175.png">

# `jsmodel`

Exports a model (e.g. a regression or classification from tidymodels) into a JavaScript widget / htmlwidget so that you can put it on a website and predict live in a user's browser. 

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

So I guess the code is
```{r}
#' Once
#'
#' @param expr The expensive expression to evaluate
#' @param file_path File path for saving the output object as an Rds file
#'
#' @return the results of expr
#' @export
#'
#' @examples
#' my_out <-
#'   runif(1000000) %>% # some expensive operation
#'   once(file_path = "saved_random_numbers.Rds") # only do it once, save output to this file.
once <- function(expr,file_path){

  if (file.exists(file_path)){
    output <- readRDS(file = file_path)
  } else {
    output <-
      eval(expr = expr)

    saveRDS(output, file = file_path)

  }

  return(output)
}
```

# `corgui`

It's an interactive correlation plot (correlation /mutual information / ...), that you can click on a square (any combination of parameters) to get a zoom in which is a scatterplot with a linear trend / cubic spline / rf regression. And yes, it's pronounced "Corgi".

<img width="264" alt="corgui" src="https://user-images.githubusercontent.com/20785842/187031767-c7f5fe13-7b0b-463c-af4b-25507b41b649.png">
