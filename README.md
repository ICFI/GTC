GTC
===

Intro to Web Mapping

Sections:
1.  Finding the Data and Downloading it From Census
2.  Joining and Cleaning the Data in ArcMap
3.  Turning the Data into a Geojson File
4.  Adding the Geojson to a Leaflet Web Map


Section 1 - Finding the Data and Downloading it From Census
1. Create a working folder on the desktop
2. Go to http://www2.census.gov/.
  a. Scroll down and select “GEO”
  b. Navigate to “Tiger”
  c. Select “TIGER2012”
  d. Click “TABBLOCK”
  e. Download “tl_2012_11_tabblock.zip” because these are the block groups for DC (FIPS STATE CODE 11)
  f. Move the downloaded file to your working folder on your desktop
2. Go to the American Fact Finder website:  http://factfinder2.census.gov/faces/nav/jsf/pages/index.xhtml.
  a. Select “Advanced Search”
  b. Then select “Show me all”
  c. Navigate to “Topics”
  d. Select the plus sign next to “Datasets” and choose the census data you are interested in. For this, we are going to pull Census 2010 SF1 data.
  e. Now in the same frame, scroll up and select the “People” grouping
  f. Select "Basic count/estimate" and the subgroup “Population Total”, and then close the frame.  The left hand box should say Sf1 2010 census & population total
  g. In the left hand pane, select the “Geographies” tab
  h. Then select the “Name” tab
  i. In the scroll select “Block” and select “within state” and choose DC
  j. In the geography results, check the box that says "All results within District of Columbia"
  k. Click "Add", then close.
  l. In the main window, select the demographics information you want to download.  In this case, select "P1 - Total Population"
  m. Select the "Download" button
  n. Move the downloaded file to your working folder on the desktop


Section 2 - Joining the data in ArcMap
1.  In the working directory, unzip both the Geo data and the tabular data.
2.  Open the population data in a text editor, preferably textpad.  Revisions appear on some lines with the population count.  You need to remove the reference to revisions, or your data will be lose when converting from text to number.
  a. Revisions are enclosed in parenthesis.  Use the find/replace feature to replace all starting parens with a comma and the paren (Replace "(" with ",(".  This breaks the revision into it's own column.
  b. CSV Files need the same number of columns for every record.  Now replace the line break character with a comma and the line break (replace "\n" with ",\n".  Make sure regular expressions are turned on).
  c. Now we have 1 too many columns on the records with revisions, so replace the close parens followed by a comma with just close parens (Replace ")," with ")")
2.  In ESRI, create a file geodatabase in your working directory, and export both datasets to it.
3.  In the demographic table, add a new String field for the FIPS code.  Calculate GeoID2 to be the fips code.  By default, the geoid2 field comes in as a number, so on states like california (06 fips) the leading zero will be dropped.
4.  Add a new number (long) field for total population, p001 will come in as a string. Calculate p001 to the new number field. 
5.  Now join the population data (on field FIPS) to the block data (on field GeoID)
6.  Export the data to a new featureclass
7.  Now add a new field (text, length of 12) called FIPS_BG.  This will be the fips code of the block groups.  Calculate this from the FIPS code field.  Only the left 12 characters (the block group identifier) will be left.
8.  Dissolve on the new FIPS_BG field, and sum the Population.



Section 3 - Turning the Data into a Geojson File
1.  We checked github, someone else already built a tool to convert data in ESRI to GeoJson.  Download this tool:  https://github.com/project-open-data/esri2open
2.  Convert your block groups to geojson


Section 4 - Adding the Geojson to a Leaflet Web Map
1.  We are just going to use a leaflet sample for this.  Go to http://leafletjs.com/examples/choropleth-example.html
2.  Save the demo as a local html file.  Re-source the libraries it is referencing to be remote libraries.




