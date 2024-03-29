# AWH-Geo
AWH-Geo tool and calculations for the paper "Global Potential of Harvesting Drinking Water from Air using Solar Energy", currently in-review at Nature.

This tool was built at X (formerly Google X) as a product requirement assessment for a novel portable water-from-air device (atmospheric water harvester or AWH). It's primary purpose is to calculate the potential for AWH to supply drinking water needs to some portion of the 2.2 billion worldwide without access. Understanding the output in L/day of a modeled device is critical for device design iteration, understanding costs per unit water volume, and user adoption. 

The tool uses a global climate timeseries at high spatio-temporal resolution (ERA5-Land at 9 km, 1-hr interval) over the ten-year period 2010-2019. Other climate data could be substituted if desired by the user. 

The tool components here are built in Google's CoLab tool using the Earth Engine Python API. Derivative data layers reside as assets in Earth Engine and are called in the tool. These data layers are also accessible separately in FigShare (DOI:10.6084/m9.figshare.13568273).

REQUIREMENTS: You must have an account with [Google Drive](https://drive.google.com/drive/my-drive) and [Earth Engine Account](https://developers.google.com/earth-engine/) with a home folder. Once signed up with Earth Engine, to create a home folder, go to the [code editor](https://code.earthengine.google.com/), click the "Assets" tab, and create a folder with a username of your choice. 

TO RUN THE TOOLS: Select a tool in the "notebooks" folder, and simply click the "Open in CoLab" icon at the top of each tool and follow the instructions. The processing will run in an open Google runtime and process through your account in Google Earth Engine.

There are four main components to the tool available here, with descriptions below:

1) Population no SMDW calculation:

Builds the data layer (image at 1 km resolution) of population without SMDW using the JMP GeoFabric (built separately, tool to build in FigShare) and the WorldPop 2017 residential population counts. Result is shown in Figures 1a-b.
  
2) AWH-Geo:

Geospatial pipeline for calculating the mean output (L/day) worldwide of any AWH device or experimental characterization. Also runs moving averages for time-based statistics for output shortfall and variability metrics. Includes a "TEST SUBSET" script which can be run in a small portion of the dataset. This tool was used to produce Figures 3a-c of the upper limit values of various AWH methods.

3) AWH-Geo_threshold:

Special-case of AWH-Geo to conduct coincidence analysis of primary climate drivers of AWH: relative humidity (rH in %) & global horizontal irradiance from sunlight (GHI in W/m^2). Also included is a version of this tool using a secondary climate timeseries (GLDAS from NASA). This was used to produce Figures 4a-b. Running the entire timeseries for all the thresholds will take a very long time and likely exceed a user's storage quota in Earth Engine. For this reason, we include here the results of this analysis: [results_thresholds.csv](https://drive.google.com/file/d/1iXAebeMBoJXvHBoOvAf73cLeeTTgsfZ_/) and [results_thresholds_adj.csv](https://drive.google.com/file/d/1-bt0NFa5lRcHX7OH2xIZ04Kytk1tldXI/) -- copy these into the root directory of your Drive folder to run the remainder of the script to produce figures for the coincidence analysis.

4) Population without SMDW by Output Scenario:

Runs a cumulative histogram by 0.5 L/day output bins of population without SMDW who live in an area above each output bin across several scenarios: 2 real devices, 1 experimental sorbent material, 2 upper limits, and 6 characteristic curves which reach a target user base (500 million, 1.0 billion, and 1.5 billion people without SMDW).

OUTPUT TABLES: An Output Table in Google Sheets and housed in your Google Drive folder is necessary to run AWH-Geo. Several Output Tables were used for the limits analysis (Figure 3a-c) and the final results (Figure 4c-d) in the paper, and [are accessible here](https://drive.google.com/drive/u/1/folders/1EzuqsbADrtdXChcpHqygTh7SuUw0U_QB). You can copy these to your Drive (to any location). Once copied to your Drive, remove the "Copy of " in the beginning of the name of the new file which now lives in your Drive. This can be then run through AWH-Geo using their CODENAME (characters after "OutputTable_" in the document name).

FIGURE CREATION: Code to produce figure 4 for paper are included and can be run as standalone script.

LICENSE: This work is covered under an Apache 2.0 license. A few external data sources and code packages are used which fall under other licensing arrangements which must be abided by the user of this tool, as follows (as of August 2021):
- ERA5-Land data set (https://apps.ecmwf.int/datasets/licences/copernicus/)
- GLDAS 2.1 data set (https://disc.gsfc.nasa.gov/information/documents?title=data-policy)
- WorldPop 2017 (https://creativecommons.org/licenses/by/4.0/)
- Google Earth Engine API (https://earthengine.google.com/terms/)
- gspread (python module) (https://github.com/burnash/gspread/blob/v3.7.0/LICENSE.txt)

For questions, please contact the paper's corresponding author Jackson Lord at jacksonlord@gmail.com
