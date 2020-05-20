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
1. Initial and final datasets for a mooring should be in same file (initial/preliminary datasets not mandatory and are more likely to exist after 2013).  The arbitrary date is based on the transition between D.Kachel and S.Bell workflow and the evolution of an extended ecoraid data archive.
2. Profile Moorings (with ADCP's or other 2D instruments) are usually gridded data and will have their own dataset descripter, these can be in the same file as the 1D tabular descriptor for that mooring.
3. Cruises should have preliminary/final/hydrographic bottles/oxygen/salinity dataset descriptors all in one xml file.  This could get large and unweildy so be careful.

The goal is to be able to cut and paste previous sets and then edit the necessary metadata to create consistent and well documented data.