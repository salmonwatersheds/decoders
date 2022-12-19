# decoders
Contains lookup files that relate PSF-assigned IDs to those used by DFO etc. for cross-referencing.

Each lookup file has two worksheets: the first contains the actual match ups of IDs and the second contains definitions and sources of the different fields. 

## How to use these files

In an attempt to centralize and streamline connections between SWP's datasets and other datasets (e.g., NuSEDS), these are the **go-to decoder files** that connect PSF-assigned `cuid` and `streamid` fields, as well as the PSE Regions, to other IDs used for CUs and streams (e.g., NuSEDS' `POP_ID` field).

To use these files, you can source them in your R code using the [`readxl` package](https://readxl.tidyverse.org/) (part of the `tidyverse` family):

``
library(tidyverse)
lookup <- read_excel()
``