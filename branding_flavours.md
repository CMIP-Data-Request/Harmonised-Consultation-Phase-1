# Branding Flavours

The branding concept has been developed in a paper by [Taylor et al.](https://docs.google.com/document/d/19jzecgymgiiEsTDzaaqeLP6pTvLT-NzCMaq-wu-QoOc/edit?tab=t.0) with the aim, among others, of promoting greater clarity and scalability in the naming of variables used in WCRP model intercompaison projects (MIPs).

## Taylor et al.

Taylor et al. propose an approach in which the brand is defined in terms of four short labels:

* TemporalLabelDD
* VerticalLabelDD
* HorizontalLabelDD
* AreaLabelDD

## Data Request Vocabularies

An alternative proposal is based more directly on vocabularies in the current request AR7 Fast Track Request (also used in the CMIP6 Data Request):

* [Spatial Shape](https://airtable.com/appBWxP0SS7K1hweJ/shrxhV6tenQBnOGRj/tblfgncqdfIq6vXWi/viw9CC8aaWk8gbbd7?blocks=bip0j1KMajP5L0L2W), "Name" element
* z-axis (in [Coordinates and Dimensions](https://airtable.com/appBWxP0SS7K1hweJ/shrxhV6tenQBnOGRj/tblDgm0SuMVzRxGdn/viwXp13lTZZFHj7dg?blocks=bip0j1KMajP5L0L2W) with Axis Flag "Z"), "Name" element
* [Cell Methods](https://airtable.com/appBWxP0SS7K1hweJ/shrxhV6tenQBnOGRj/tblfeKAK8hs8sfutp/viwb6wgTMTHLyNFBL?blocks=bip0j1KMajP5L0L2W), "Label" element

### Notes
* Once a cell methods string is specified from the list, there is only one valid choice of time axis. This was not enforced in CMIP5/6, and is yet enforced in the CMIP7 beta release, but can be enforced for the full 1.0 release.
* The "Coordinates and Dimensions" vocabulary distinguishes between NetDCF dimensions (which determine the size of an array) and coordinates, which give additonal descriptive metadata. For many purposes this distinction is not relevant, but it is important if we want to explain to users the significance of the metadata that is used to specify file format.
* The short codes referenced above were introduced in CMIP6 for convenience, but did not always follow a regular pattern. They have been cleaned up for CMIP7.

## Implementation

Both are implemented in the AR7 Fast Track Data Request, and can be seen in the [working copy of the data request](https://airtable.com/appBWxP0SS7K1hweJ/shrxhV6tenQBnOGRj), with the Taylor et al. approach labelled "Brand (WIP)" and the alternative labelled "Brand (DR)". 

The "Brand (WIP)" approach produces 125 different values (including several for metadata combinations which are incomplete at this stage); the "Brand (DR)" approach has 164 different values. In some cases there is a one-to-one correspondence: e.g. "tavg-l-hxy-sea" matches "tmn-ol-hxy-amns" exactly. In other cases the WIP version maps onto multiple DR versions.

The key advantage of the DR version is that each "brand" corresponds to a unique combination of cell methods, spatial amd temporal dimensions. This gives it greater simplicity in implementation and greater utility:

* The existing vocabularies are used in the design and maintenance of the variable registry, ensuring strong consistency across variables. For instance, the majority of new variables proposed for the CMIP7 request use existing coordinates and dimensions and this ensures validity of the CF metadata. Using terms which are already in the registry, rather than adding new ones, minimises the need for additional documentation.
* It would be confusing to users to have multiple vocabularies having almost the same information. 
