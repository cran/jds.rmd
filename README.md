# jds.rmd

[![CRAN_Status_Badge][r-pkg-badge]][cran-url]
[![R build status][gha-icon]][gha-url]


## Overview

The R package **jds.rmd** provides R Markdown templates intended for
[Journal of Data Science][jds-url], which can be useful for authoring
a manuscript with code chunks or producing tables/figures on the fly.

## Installation

### Option 1

One can install the released version from [CRAN][cran-url].

```R
install.packages("jds.rmd")
```

### Option 2

The latest version of the package can be installed by using **remotes**:

```R
if (! require(remotes)) install.packages("remotes")
remotes::install_github("wenjie2wang/jds.rmd", upgrade = "never")
```

## Getting Started

We can create a manuscript draft named `my_draft.Rmd` and render it to PDF as
follows:

```R
draft_rmd <- "my_draft.Rmd"
jds.rmd::draft(draft_rmd)
rmarkdown::render(draft_rmd)
```

Notice that all the edits should be done in the R Markdown file `my_draft.Rmd`.
The LaTeX source file generated by *pandoc* is kept on purpose for submission
and may help debug possible compilation errors.
The generated PDF will be sufficient for the peer-review process.
If the paper is accepted, we will only need to provide the journal production
team with the generated LaTeX source together with the generated figure files if
any.


The package contains two class files, `jdsart.cls` and `jds.cls`.
The former is the latest version developed by [VTeX][jdsart-cls] and thus
recommended; the latter is deprecated and was developed before having the
production support by VTeX.
The function `jds.rmd::draft()` creates a draft using the `jdsart.cls` by
default.
A draft using the `jds.cls` can be created by specifying `cls = "jds"`.
For those users who use the latest **jds.rmd** package but the deprecated class
file, an option `cls: jds` needs to be added to the YAML header as follows:

```YAML
output:
  jds.rmd::pdf_article:
    cls: jds
```

[r-pkg-badge]: https://www.r-pkg.org/badges/version/jds.rmd
[cran-url]: https://CRAN.R-project.org/package=jds.rmd
[gha-icon]: https://github.com/wenjie2wang/jds.rmd/workflows/R-CMD-check/badge.svg
[gha-url]: https://github.com/wenjie2wang/jds.rmd/actions
[jds-url]: https://jds-online.org
[jdsart-cls]: https://github.com/vtex-soft/texsupport.ruc-jds
