# SNAP Desert Atlas

Every census tract in the United States where at least 15% of households receive SNAP and no
full-service SNAP-authorized store lies within USDA's food desert distance of the tract's
population-weighted center.

**[Open the atlas](https://syedmfuad.github.io/snap-desert-atlas/)** &middot; **[Read the results](https://syedmfuad.github.io/snap-desert-atlas/results.html)**

## What a SNAP desert is here

A tract qualifies when both hold:

- **Need.** At least 15% of households received SNAP benefits (ACS 2019-2023 five-year estimates).
- **Access.** No supermarket, large grocery store, or super store authorized to accept SNAP lies
  within half a mile of the population-weighted tract center in urban tracts, or ten miles in rural
  ones (USDA Food and Nutrition Service authorized retailer file, stores active 31 December 2024).

The distance thresholds, the aggregation rule, and the vehicle-access rule are the benchmarks USDA
uses to define food deserts in the Food Access Research Atlas. The 15% participation cutoff is this
study's own, because USDA screens need by income rather than by participation; so are the urban
density rule, the full-service store universe, and the severity tiers.

This is a monitoring measure, not evidence of unmet need. It marks where benefit holders are
concentrated and full-service stores are not. It does not observe where any household shops, what it
pays, or whether it is food secure.

## Using the atlas

The national view draws every desert tract plus the tracts USDA's vehicle-access rule adds, colored
by severity. Selecting a state loads that state at full resolution: all high-participation tracts,
with served tracts in grey, plus store locations. Click a tract for its SNAP share, distance to the
nearest full-service store, distance to the nearest store of any format, carless share, and policy
flags. Filters isolate the three tiers, the vehicle rule, and the three policy groups from the paper.

Geometry loads in two tiers so the page opens quickly: a simplified national layer first, then each
state's full-resolution file on demand. All tracts in one file would run to roughly 260 MB.

## Sources

| Source | Use |
| --- | --- |
| USDA FNS SNAP Authorized Retailer file | store locations, formats, authorization dates |
| Census ACS 2019-2023, table B22010 / B992512 | SNAP participation by tract |
| Census ACS table B08201 | vehicle availability |
| Census TIGER/Line, 2020 vintage | tract and state geometry |
| Census Centers of Population | population-weighted tract centers |
| USDA ERS Food Access Research Atlas | food desert comparison |

Basemap tiles &copy; [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors,
&copy; [CARTO](https://carto.com/attributions). Mapping by [Leaflet](https://leafletjs.com/).

## Rebuilding

This directory is generated, not edited. From the pipeline root:

```
python 24_build_map_data.py      # tract geometry -> outputs/map_data/
python 25_build_map_page.py --web  # the atlas, web target
python 26_build_site.py          # assemble site/
```

`25_build_map_page.py` without `--web` builds the self-contained copy, which carries no basemap
because its host admits no tile servers.

## Status

Working-paper material under review. Figures may change as the manuscript is revised; the
replication package, not this site, is the citable record.
