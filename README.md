# PA_2010_2018
 PA election data 2010-2018
combines the mggg shapefile for Pennsylvania - see https://github.com/mggg-states/PA-shapefiles
and the documented fields therein


with openprecincts.org PA shapefile - https://openprecincts.org/pa/
with election results: ['G18DemSen','G18RepSen','G18DemGov','G18RepGov']  

with the following edits to openprecincts data:
for compatibility with mggg database and census blocks, CRS/ coordinate system transformed to 
EPSG:4269 - NAD83 - Geographic

VTD in rows 3148 and 3292 were defective, so replaced with their equivalent in mggg database, 830 and 3274 respectively.

- Population data from census block level was downloaded from NHGIS.org. Population data from blocks then aggregated into openprecincts geopanda dataframe at VTD level

- as maup would not work with openprecincts data, a mapping was created identifying, using shapely functions, which census block was within which openprecincts VTD.
- the mapping was used to disaggregate, pro-rating by population ratio, election results from openprecincts VTD's --> census blocks

- using a mapping from maup identifying which census blocks were in which mggg VTD's, vote totals were aggregated from census blocks --> mggg VTDs.

- the zipfile is the shapefile resulting from the above mapping together with the pre-exisding mggg data
