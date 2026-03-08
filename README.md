# New-Zealand-Watershed-Analysis

The goal of this project was to analyze digital elevation data from a set of watersheds along the western flank of the Southern Alps of New Zealand. The study focused on watersheds located in the immediate hanging wall of the Alpine Fault, where rapid tectonic uplift driven by fault motion coincides with active fluvial and glacial erosion of the landscape. One of the objectives was to examine how various calculated values differ across watersheds and what these differences reveal about the ways rivers and glaciers may have shaped the surface of each watershed.

## Background
Watershed analysis involves examining the landscape and hydrology of land areas where surface water drains to a common outlet, such as a river, lake, or ocean. In this study, the focus was on understanding how factors such as watershed area and topographic relief vary across a set of river watersheds in the Southern Alps, with the aim of exploring relationships between landscape uplift and erosion. To achieve this, a series of quantitative values were calculated for each watershed and subsequently analyzed to assess spatial variability within the study area. The analysis required several steps, including loading digital elevation data for the region, delineating the watersheds of interest, evaluating the landscape characteristics of each watershed, and visualizing the results. The following sections provide a detailed examination of these processes and demonstrate how watershed analysis can be performed using Python.

## Methodology
Watershed delineation involves identifying all points that lie upstream (or upslope) of a specified outlet on a digital elevation model (DEM). Outlet points can be determined in various ways; in this case study, they were selected visually using Google Maps by identifying locations where rivers along the western side of the New Zealand Alps, between approximately 42.4°S and 44.0°S, exit their valleys. This latitude range roughly corresponds to a linear segment of the Alpine Fault, which forms the boundary between the Australian and Pacific tectonic plates.

After outlet points are identified, several preprocessing steps are required to ensure that watersheds can be accurately defined. Specifically, the DEM must be conditioned so that water flow paths can be determined, assuming that water moves to neighboring cells of lower elevation. This initial preprocessing is collectively referred to as hydrological conditioning and includes the following steps:

1. `Filling pits:` Pits are individual cells in the DEM with no neighboring cell at a lower elevation. Their elevations must be increased so that water can flow toward at least one neighboring cell.
2. `Filling depressions:` Depressions are groups of cells lacking an outlet. Their elevations must similarly be adjusted to allow drainage to a downstream cell.
3. `Resolving flats:` In flat regions, such as lakes, water cannot flow downhill. These areas must be modified to establish a continuous flow path toward the outlet.

Once the DEM has been conditioned, additional steps are performed using the updated DEM to generate the necessary information for watershed delineation:

- Determining flow directions: This step identifies the direction in which water would flow from each DEM cell, enabling tracing upstream from the outlet to delineate watershed boundaries.
- Determining flow accumulation:Flow accumulation calculates the number of upstream cells draining into each DEM cell. While not strictly required for watershed delineation, it can assist in identifying river channels, especially when outlet points are not located precisely on a channel cell.

Following these procedures, it becomes possible to delineate the watershed upstream of the specified outlet point accurately.
