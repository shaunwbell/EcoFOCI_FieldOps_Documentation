# Internal Data Distribtuion

## Pavlof file-tree

## ERDDAP (Akutan/Downdraft/Thundersnow)

The servers listed in the heading above are the initial primary list of erddap servers run internally.

1. Akutan - intended to be the operational server (limited updates and well tested, not taken offline frequently).  This is a CNSD managed VPN system running a variant of RHEL
2. Downdraft/Thundersnow - development server with more data but more frequent testing and not guaranteed to be up at all times.  This is a system run by S.Bell in office (Mac OS)

### setup.xml

Each ERDDAP server needs to have its setup.xml file developed for its specific intentions.  Look at the installed version /{path_to_tomcat}/content/erddap/setup.xml and review the installation instructions from Bob Simmons.  Details regarding memory management, high level erddap managament and security and file/os interactions are spelled out here.

### datasets.xml

Each ERDDAP server needs to have its datasets.xml file developed for the specific datasets to be available on that server.  PMEL/EcoFOCI is currently using a repository and suggesting subsetting the datasets.xml into logical units (all datasets in a cruise or a moored location are in one sub xml file appropriatly named.  These files are then concatenated into the master datasets.xml file to be used.  Downdraft/(Thundersnow) and Akutan have github repositories available at [Github](https://github.com/NOAA-PMEL/EcoFOCI_FieldOps_Documentation/tree/master/erddap_xml) - please review the current collection prior to submission of a new dataset.  Little to no vetting of files is performed prior to concatenation.

Suggeted subsetting:
1. Initial and final datasets for a mooring should be in same file (initial/preliminary datasets not mandatory and are more likely to exist after 2014).  The arbitrary date is based on the transition between D.Kachel and S.Bell workflow and the evolution of an extended ecoraid data archive.  
2. Profile Moorings (with ADCP's or other 2D instruments) are usually gridded data and will have their own dataset descripter, these can be in the same file as the 1D tabular descriptor for that mooring.  Due to QC procedurs, ADCP final vel data and ADCP final ein data should be provided seperately (if ADCP preliminary data is to be provided, this may be able to be granted in the same dataset)
3. Cruises should have preliminary/final/hydrographic bottles/oxygen/salinity dataset descriptors all in one xml file.  This could get large and unweildy so be careful.

The goal is to be able to cut and paste previous sets and then edit the necessary metadata to create consistent and well documented data.

**POINTS to WATCH for in datasets.xml**

1. MissingValue = 1e35 (often for FOCI - this is a value chosen to make math impossibly large and to remove invalid data, but it also is a standin for missing data) - alternatively `_FillValue` should\could be set to 1e35.  Play and test your dataset for this to make sure missing values are properly being addressed.  Occasionally a -9999 exists instead of a 1e35 (there is not a consistent distinction between the two).  In these cases missing should be -9999 and fill should be 1e35 (or internally defined if possible)
2.  All initial files that are used to make the archive dataset must have CF compliant timewords (EPIC 2-word time words will fail)

** xml file characteristics **
1.  A mooring site may have 2-3 datasets associatied with it (ADCP gridded, tabular timeseries - both preliminary and final, and timeseriesprofile if prawler-like).  Each site is broken into its own dataset subset for ease of editing.
2.  A cruise may have 3-4 datasets associated with it (preliminary CTD, final CTD, hydrographic bottles, shiptrack)
3.  Some files are generated based on existing erddap datasets.  These are "backups" that are archived in netcdf format and gridded products from tabular products.  Since both are dynamically driven, they are not archived in the EcoRAID structure, but instead on a seperate location (currently downdraft/thundersnow)