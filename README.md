[![Project Status: Concept – Minimal or no implementation has been done
yet, or the repository is only intended to be a limited example, demo,
or
proof-of-concept.](https://www.repostatus.org/badges/latest/concept.svg)](https://www.repostatus.org/#concept)

TanDEM-R
========

R interface for downloading TanDEM-X data. Information on the data can
be found at [DLR's
geoservice](https://geoservice.dlr.de/web/dataguide/tdm90/ "geoservice.dlr.de").

Basic idea is to enable such a workflow to handle TanDEM-X data:

    options("geoservice.usr" = "Max.Mustermann@mail.com")

    tiffiles <- download_TanDEM()

    library("stars")
    vrt <- st_mosaic(tiffiles)
    x <- read_stars(vrt, proxy = TRUE)
    plot(x)

    ## Loading required package: abind

    ## Loading required package: sf

    ## Linking to GEOS 3.8.0, GDAL 3.0.4, PROJ 7.0.0

![](README_files/figure-markdown_strict/map-1.png)

Installation
------------

Via [**Devtools**](https://devtools.r-lib.org) one-liner with specifying
`subdir = "pkg"`:

    devtools::install_github("meteosimon/TanDEM-R", subdir = "pkg")

Authentification at DLR geoservice
----------------------------------

First, you have to register at
[DLR](https://sso.eoc.dlr.de/tdm90/selfservice/). Within the package I
use [**keyring**](https://github.com/r-lib/keyring#readme) for handling
authentification. The default for the keyring service is
`"geoservice.dlr"`.
