# Cruise CTD Processing - EcoFOCI

## Cruise Data

This list is not exhaustive and may vary from vessel to vessel.

- CTD data (ocasionally bongo/fastcat or sbe-19 data)
- GPS
- CTD Records, event records

Other cruise associated data such as underway data, may be found in the "AlongTrack" portion of the EcoFOCI data archive.

## Cruise MetaData

EcoFOCI, FOCI, EMA all maintain seperte databases.  a fairly simple MariaDB iteration of CTD cast logs, MasterCod, and CLAMS.  Be sure to insert your metadata into those as thouroughly as possible.  In the case of EcoFOCI, the database is used as the source for metadata information within the archived datafiles.  It can also be used to generate quick plots of poistion, sampling intensity (as a function of date/time) and other useful metrics not associated with the actual CTD data.

- ***Make a Cruise Map***
- ***Add to FOCI database for web display***
  
## SBE Preliminary Processing


## Initial Visualizations


## Furthur QC 

- justify and apply salinity offsets
- justify and apply par/chlor __zero__ offsets
- justify and apply oxygen __slope__ correction (per SBE Tech note via winklers)

- be sure to track edits/changes in data.  Ultimate goal is for any dataset to be reproducible.

- usually singleton points are interpolated through, multiple bad points are QC-removed


## Recalculation of any dependent QC'd parameters


## Convert to FOCI archival format

- This is a CF compliant netcdf file that can be hosted by an erddap server of the QC'd **downcast** data.
- This is a CF compliant netcdf file that can be hosted by an erddap server of the unQC'd **bottle** data.
- This is a CF compliant netcdf file that can be hosted by an erddap server of the QC'd **nutrient bottle** data.
- This is a CF compliant netcdf file that can be hosted by an erddap server of the QC'd **oxygen bottle** data.
- This is a CF compliant netcdf file that can be hosted by an erddap server of the QC'd **chlorophyl bottle** data.

There may be other data streams not consistently archived with EcoFOCI that have CTD affiliations

## 
