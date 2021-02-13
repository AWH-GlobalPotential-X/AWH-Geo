# AWH-Geo
AWH-Geo tool and calculations for the paper Global Potential of Harvesting Drinking Water from Air using Solar Energy.

This tool was built at X (formerly Google X) for a product design requirement assessment and market analysis for a novel portable water-from-air device (atmospheric water harvester or AWH) for supplying drinking water needs to some portion of the 2.2 billion worldwide without access. Understanding the output in L/day of a modeled device is critical for product design iteration to drive down costs per unit water and increase adoption. 

The tool uses a global climate timeseries at high spatio-temporal resolution (ERA5-Land at 9 km, 1-hr interval) over the five-year period 2013-2018. Other climate data could be substituted if desired by the user. 

The tool components here are built in Google's CoLab tool using the Earth Engine Python API. Derivative data layers reside as assets in Earth Engine and are called in the tool. These data layers are also accessible separately in FigShare (DOI:10.6084/m9.figshare.13568273).

TO RUN THE TOOLS: Simply click the "Open in CoLab" icon at the top of each tool and follow the instructions. The processing will run in an open Google runtime and process through your account in Google Earth Engine.

There are four main components to the tool available here, with descriptions below:

1) Population without SMDW calculation:

Builds the data layer (image at 1 km resolution) of population without SMDW using the JMP GeoFabric (built separately, available in FigShare) and the WorldPop 2017 residential population counts. Result is shown in Figures 1a-b.
  
2) AWH-Geo:

Geospatial pipeline for calculating the mean output (L/day) worldwide of any AWH device or experimental characterization. Also runs moving averages for time-based statistics for output shortfall and variability metrics. Includes a "TEST SUBSET" script which can be run in a small portion of the dataset. This tool was used to produce Figures 2a-c of the upper limit values of various AWH methods.

3) AWH-Geo_threshold:

Special-case of AWH-Geo to conduct coincidence analysis of primary climate drivers of AWH: relative humidity (rH in %) & global horizonatl irradiance from sunlight (GHI in W/m^2). Also included is a version of this tool using secondary population (LandScan 2017 from ORNL) and climate timeseries (GLDAS from NASA). This was used to produce Figures 3a-b.

4) Population without SMDW by Output Scenario:

Runs a cumulative histogram by 0.5 L/day output bins of population without SMDW who live in an area above each output bin across several scenarios: 2 real devices, 1 experimental sorbent material, 2 upper limits, and 6 characteristic curves which reach a target user base (500 million, 1.0 billion, and 1.5 billion people without SMDW).

OUTPUT TABLES: An Output Table in Google Sheets and housed in your Google Drive folder is necessary to run AWH-Geo. 

Several Output Tables were used for the limits analysis (Figure 2a-c) and the final results (Figure 3b-c) in the paper, and are accessible here: https://drive.google.com/drive/folders/1z1V1nGLJy9g7SSvizrahmGd5imDGq5lR?usp=sharing. You can copy these to your Drive. Once copied to your Drive, these preloaded Output Tables can be run through AWH-Geo by entering their CODENAME (characters after "OutputTable_" in the document name).


For questions, please contact the paper's corresponding author Jackson Lord at jacksonlord@gmail.com
