GoM-Series Regions
================

``` r
suppressPackageStartupMessages({
  library(sf)
  library(dplyr)
})
source("setup.R")
```

Region definitions are adapted from
[MarineRegions.org](https://www.marineregions.org/gazetteer.php?p=details&id=8940).
The “North Coastal Shelf” extends from northern Massachusetts to Grand
Manan at the mouth of Fundy Bay. We split this region at Penobscot Bay
into “Western Coastal Shelf” and “Eastern Maine Coastal Shelf”.

``` r
x = read_regions(keep = 'all')
plot(x,  
     main = "Gulf of Maine Regions", 
     axes = TRUE,
     key.width = lcm(7),
     key.pos = 4)
```

![](README-regions_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

We opt to use a smaller selection of the available regions by default:
“Wikinson Basin”, “Jordan Basin”, “Georges Basin”, “Georges Bank”,
“Eastern Maine Coastal Shelf” and “Western Coastal Shelf”. Note below
that we drop the use of the `keep = 'all'` to get the subset.

We provide options for loading as bounding boxes…

``` r
bboxes = read_regions(form = 'bbox')
plot(x,  
     main = "Gulf of Maine Regions", 
     axes = TRUE,
     key.width = lcm(7),
     key.pos = 4,
     border = NA,
     reset = FALSE)
plot(st_geometry(bboxes), add = TRUE)
```

![](README-regions_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

… or convex hulls…

``` r
chulls = read_regions(form = 'chull')
plot(x,  
     main = "Gulf of Maine Regions", 
     axes = TRUE,
     key.width = lcm(7),
     key.pos = 4,
     border = NA,
     reset = FALSE)
plot(st_geometry(chulls), add = TRUE)
```

![](README-regions_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->
