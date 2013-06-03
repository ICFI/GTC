GTC
===

Intro to Web Mapping

Sections:
1.  Finding the Data and Downloading it From Census
2.  Joining the Data in ArcMap
3.  Turning the Data into a Geojson File
4.  Adding the Geojson to a Leaflet Web Map


Finding the Data and Downloading it From Census

1. Create a working folder on the desktop named “Temp Data Folder” and move the downloaded block zip to it
2. Go to http://www2.census.gov/.  \n
\ta. Scroll down and select “GEO”\n
\tb. Navigate to “Tiger”\n
\tc. Select “TIGER2012”\n
  d. Click “TABBLOCK”
  e. Download “tl_2012_11_tabblock.zip” because these are the block groups for DC (FIPS STATE CODE 11)

2. Go to the American Fact Finder website:  http://factfinder2.census.gov/faces/nav/jsf/pages/index.xhtml.
  a. Select “Advanced Search”
  b. Then select “Show me all”
  c. Navigate to “Topics”
  d. Select the plus sign next to “Datasets” and choose the census data you are interested in. For this, we are going to pull Census 2010 SF1 data.
  e. Now in the same group, scroll up and select the “People” grouping
  f. Select Basic count/estimate and the subgroup “Population Total”.  The left hand box should say Sf1 2010 census & population total

3.  In the left hand pane, select the “Geographies” tab
  a. Then select the “Name” tab
  b. In the scroll select “Block” and select “within state” and choose DC

