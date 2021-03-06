
[![Build Status](https://travis-ci.org/reconhub/recontools.svg?branch=master)](https://travis-ci.org/reconhub/recontools) [![Build status](https://ci.appveyor.com/api/projects/status/wn4un3v2e3owts4l/branch/master?svg=true)](https://ci.appveyor.com/project/dirkschumacher/recontools/branch/master) [![Coverage Status](https://img.shields.io/codecov/c/github/reconhub/recontools/master.svg)](https://codecov.io/github/reconhub/recontools?branch=master) [![CRAN\_Status\_Badge](http://www.r-pkg.org/badges/version/recontools)](https://cran.r-project.org/package=recontools)

Tools to develop RECON packages
===============================

Installation
------------

### CRAN

Not yet on CRAN

### Development version

To install the most recent development version use:

``` r
devtools::install_github("reconhub/recontools")
```

What does it do?
----------------

### Package scaffolding

When starting a new RECON package, you can use `init_package` to quickly create a default package structure:

``` r
# from within your session
recontools::init_package("mynewpackage")

# you can also set a specific path for the new package
recontools::init_package("mynewpackage", path = "my_new_package_dir")

# you can also disable the CRAN checks
recontools::init_package("mynewpackage", check_cran_name = FALSE)
```

In case you want to create a new package from the command line, run:

    Rscript -e "recontools::init_package('mynewpackage')"

Please note that using `Rscript` creates all optional components (like the MIT license) without asking.

`init_package` currently does the following:

-   Checks if the package name is valid and already taken on CRAN
-   Initializes a git repository, if not already present
-   Creates default `.Rbuildignore` and `.gitignore` files
-   Creates an `R` directory
-   Creates a default `DESCRIPTION` file
-   Adds an MIT License (asks for it)
-   Adds `testthat` tests
-   Adds a code of conduct (from the `usethis` package)
-   Creates a default `README.Rmd`
-   Creates a sample vignette
-   Adds travis CI + codecov (asks for it)
-   Adds appveyor (asks for it)
-   Adds a default `.lintr` file
-   Adds a `NEWS.md` file
-   Runs `devtools::document()`

### Package checks

You can also run package checks for a given package.

``` r
# from within your session in a package directory
recontools::check_package()

# to enable goodpractice::gp checks do
recontools::check_package(run_gp = TRUE)
```

Currently, `check_package` does the following:

``` r
recontools::check_package(run_gp = FALSE)
#> Running RECON specific tests:
#>    x Packages should have at least one rmarkdown vignette
#>    ✓ Packages should not import functions in NAMESPACE but use :: instead
#>    ✓ Packages should have a NEWS.md file
#>    ✓ Packages should have tests
#>    ✓ Packages should use roxygen2
#>    ✓ Packages should use snake case in exported functions
#>    ✓ Packages should have a URL in the DESCRIPTION
#>    ✓ Packages should have a URL for bugreports in the DESCRIPTION
#>    x Packages should have a docs folder or a gh-pages branch.
#>    ✓ Packages should use travis CI for Linux/Mac testing
#>    ✓ Packages should use appveyor CI for Windows testing
#> 
#> Consider fixing the issues identified above.
#> However, your package is already phenomenal!
```

Inspiration
-----------

This package is inspired by the [goodpractice](https://github.com/MangoTheCat/goodpractice) and the [devtools](https://github.com/hadley/devtools) package. In particular it relies on many functions provided by the `devtools` package.
