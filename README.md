# decoders
Contains lookup files that relate PSF-assigned IDs to those used by DFO etc. for cross-referencing.

Each lookup file has two pieces: the first contains the actual match ups of IDs and the second (`_definitions`) contains definitions and sources of the different fields. 


## How to use these files

In an attempt to centralize and streamline connections between SWP's datasets and other datasets (e.g., NuSEDS), these are the **go-to decoder files** that connect PSF-assigned `streamid`, `cuid`, `duid` fields, as well as the PSE Regions, to other IDs used for CUs and streams (e.g., NuSEDS' `POP_ID` field).

To use these files, you can source them in your R code directly from this GitHub repo. For example:

```
url <- "https://raw.githubusercontent.com/salmonwatersheds/decoders/main/all_regions_cu_du_smu_decoder.csv"

lookup <- read.csv(url)

```

## Different units and scales of reporting for Pacific salmon population data

These decoder files attempt to relate the following different salmon population units that are either used by different agencies/organizations (e.g., DFO versus COSEWIC), for different types of information (e.g., catch vs spawner abundance data), or represent different levels in the complex hierarchical population structure of Pacific salmon. 

|Unit|Definition|Related fields in decoders|
|---|---|---|
|Stream or river populations|Unique combinations of freshwater location, species, and (in some cases) run-timing reported in [NuSEDS](https://open.canada.ca/data/en/dataset/c48669a3-045b-400d-b730-48aafe8c5ee6). May be considered the finest scale at which salmon population data are reported.|`POP_ID`, `streamid`|
|Conservation Units|In the [Wild Salmon Policy (2005)](https://www.pac.dfo-mpo.gc.ca/fm-gp/salmon-saumon/wsp-pss/index-eng.html), a *Conservation Unit* is a group of wild salmon sufficiently isolated from other groups that, if extirpated, is very unlikely to recolonize naturally within an acceptable time frame, such as a human lifetime. Originally defined by [Holtby and Ciruna (2007)](http://www.dfo-mpo.gc.ca/csas-sccs/publications/resdocs-docrech/2007/2007_070-eng.htm).|`FULL_CU_IN`, `CU_Name`, `cuid`...|
|Stock Management Unit (SMU)|A ‘group of one or more CUs that are managed together with the objective of achieving a joint status’, meaning harvest control rules would apply to the aggregate, at least in a coarse sense. The SMU does not preclude considerations related to conserving CU-level diversity, but rather is a practical aggregation of CUs for harvest planning purposes. That is, it is the scale at which a harvest management plan, or, better, a management and assessment procedure, is developed. In many cases, elements of the PA will be implemented at finer scales of organization within a SMU. The point of developing SMU-specific targets would be to ensure that the cumulative impacts of mixed-stock and terminal fisheries are sustainable.
 |`SMU`|
|Designatable Unit|[Defined by COSEWIC](https://www.cosewic.ca/index.php/en-ca/reports/preparing-status-reports/guidelines-recognizing-designatable-units.html) as a unit of Canadian biodiversity that is discrete and evolutionarily significant, where discrete means that there is currently very little transmission of heritable (cultural or genetic) information from other such units, and evolutionarily significant means that the unit harbours heritable adaptive traits or an evolutionary history not found elsewhere in Canada.|   |
|Outlook Unit|   |   |
|PSE Region|Spatial region defined by PSF for organizing and displaying data in the [Pacific Salmon Explorer](www.salmonexplorer.ca)|`PSE_region`|
|Outlook Unit|??|`OU No.`, `Outlook Unit Name`|
|Pacific Fishery Management Unit (PFMA)|Also known as *Statistical Areas*, these are divisions of Canadian fisheries waters and the scale at which commercial catch is reported.|`Area`|


<!---  
# Not a 1:1 for CU-DU
# Each row is a unique combination of CU-DU
# Cases where part of DU is in one CU and part is in another
# Need a flag to specify the relationship between CU-DU
# - is it a 1:1, nested one way or the other, or more complicated
# - this is currently missing (coded 1-4)
# - Brendan asked what the examples of it getting wi
# Connects with SARA project - need for formal CU/DU decoder
# Carrie has her own decoder file
# Talk to Vesta about spatial data and appraoch to defining CUs
# ** Correcting mistakes - do we do this code wise
# Aiming to send CU/DU maps to COSEWIC secreteriat
# 
--->
