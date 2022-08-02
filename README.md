# r-package-ideas
Things that should be, but aRen't (yet).

# `notly`

Notly would have a single function, `notly::notly()` which is basically the inverse function to `plotly::ggplotly()`, i.e. it turns a plotly plot back into a ggplot object.

This way if you've saved an interactive plotly object you can recover the ggplot from it!

Probably this would be hard to do unless - you overwrote the ggplotly function with `notly::ggplotly()` to also save the ggplot object. That way it can simply be extracted and not reverse engineered.

# `git-shame`

Git shame will to a simmilarity search on your code, and match lines of code with stack overflow answers if they are above a certain threshold. It can then (optionally) add a comment in the code to indicate where you shamelessly stole it from.

# `faker`

Faker would either invent a fake data set from scratch with certain configurable parameters, or copy an existing dataset's structure but replacing the values.

This would be useful, for example, when the poriginal dataset is not allowed to be shared, e.g. private medical records could have the names and values replaced so that someone else could prototype a model/some code with the correct structure of the data, when they don't have access to the confidential data itself.

Further improvements could be to try to match the statistical distribution of the fake replacement data to the original data under certain assumptions.

# `namer`

Generates good names for R packages and functions by finding memorable short words that aren't taken already on CRAN or as functions in popular packages, using thesaurus/dictionary or adding in the letter R in the package name the way people seem to do.
