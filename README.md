[![Build Status](https://travis-ci.org/meireles/spectrolab.svg?branch=master)](https://travis-ci.org/meireles/spectrolab)

# spectrolab

The package is being actively developed and the *API will likely change*. You’re welcome to give it a spin, but do so *at your own risk*.

## Installation

You can install spectrolab from github with:

```R
# install.packages("devtools")
devtools::install_github("annakat/spectrolab")
```

_Note for windows users:_ Apparently there is a bug in devtools' `install_guithub` preventing the correct installation of all dependencies. If you run into trouble, try running `install.packages("prospectr")` before installing `spectrolab`.

## Using `spectrolab`

This vignette [introduces the package](vignettes/introduction_to_spectrolab.md), and works you through the basics of the package.

A vignette on how to [process spectra](vignettes/processing_spectra.md) using `spectrolab` explains how to exclude bad measurements, smooth, and normalize spectra among other things.

We highly encourage you to read the vignette on [advanced spectrolab use](vignettes/advanced_spectrolab.md) if you're planning on contributing to or developing a package that depends on `spectrolab`.


