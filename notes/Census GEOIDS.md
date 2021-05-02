<span style="font-family: Jost; text-align: justify">

<h3 style="color:#39c">Census GEOIDs and How They Work</h3>

#### 1. What are GEOIDs?
The Census Bureau (and other state/federal agencies) assign geographic identifies, or GEOIDs, to geographic entities to facilitate the organization of geographic and statistical data. These numeric GEOID codes can identify any administrative/legal geographic area all the way from states to counties, tracts, block groups, blocks, etc.

#### 2. GEOID Structure for Geographic Areas
The Census Bureau provides shapefiles that can be used for GIS processing and visualization. Each polygon in these shapefiles represents a legal/statistical geographic area and is assigned a unique GEOID. THe GEOID structure in these TIGER/Line Shapefiles provided by the Census Bureau obeys a certain hierarchal structure. A detailed description is available <a href="https://www.census.gov/programs-surveys/geography/guidance/geo-identifiers.html"><b>here</b></a>.

| Area Type | GEOID Structure | # of Digits | Area Name | GEOID          |
| --------- | --------------- | ----------- | --------- | -------------- |
| State     | STATE           | 2           | Texas             | 48     |
| County    | COUNTY          | 3           | Harris County, TX | 201    |
| Census Tract | TRACT        | 6           | Census Tract 2231 | 223100 |
| Block Group  | BLOCK GROUP  | 1           | Block Group 1     | 1      |
| Block        | BLOCK       |  4           | Block 1050        | 1050   |

The table above shows the typical structure of GEOIDs for a Census Block. A State is represented with a 2-digit code, a County with a 3-digit code, a Tract with a 6-digit code, a Block Group with a 1-digit code, and a Block with a 4-digit code. When we sum up these numbers of digits, we end up with 2+3+6+4=15, that is, a Census Block has a 15-digit GEOID that is unique to itself (See that the block group code is not included in the Census Block GEOID because the first digit of a Census Block represents the Block Group code).

Another way to represent this hierarcy could be STATE|COUNTY|TRACT|BLOCK ---> 48|201|223100|1050.

#### 3. Boundaries of Census GEOIDs

While it is intuitive to think of Census Blocks as the smallest geographic area defined by the Census Bureau that describes a population, there are some unexpected quirks about this data that one might not anticipate.

* Consider the Census Block might with the 15-digit GEOID code of 120879900000136. This is a Census Block (0136) in Monroe County (087), Florida (12) that is home to all the Keys including Key West and Key Largo. One may think that the Census Bureau divides up the Monroe County into pieces that only includes land, this is not the case. For example, <a href="http://proximityone.com/geo_blocks.htm"><b>this link</b></a> suggests that the Block with the GEOID 120879900000136 is completely surrounded with water, because all Block numbers beginning with a zero (0136 in the above example) are <b>water-only areas</b>.

* However, this isn't always useful to work with as leading zeros for a Census Block number may make it impossible to differentiate whether a certain block is a water-only area or not. Fortunately, the Census Bureau shapefiles also contain two properties called "ALAND" and "AWATER" that measure the land area and water area of each geography, respectively. These variables are more reliable to differentiate between water-only areas vs. not.

</span>
