# Table of Contents for Cruise

## EcoFOCIpy_cruisemaps: 
Station map plots of cruise including ability to plot bottom or surface on bathymetry or just plane background
## EcoFOCIpy_sbe_ctd_btlfile
Generate Bottle Files as NetCDF files from btl files
## EcoFOCIpy_sbe_ctd_btlfile_oxy/nut
Generate Bottle Files as NetCDF files from oxy and nut files (often processed independently and after the electronic measurements) for archive.  Process can be expanded to any discrete measurement like, Chlor, pCO2, etc
## EcoFOCIpy_ctd
Initial CTD procesing of cnv files
## EcoFOCIpy_ctd_xx_QC
Apply manual edits from .csv files to netcdf files.  Usually despiking, deleting data, linear interpolation.  Recalculate a few parameters (sigma, oxyconc, etc) that will be impacted by changes in primary vars.
## EcoFOCIpy_ctd_samplecor
Apply Corrections from secondary sampling
- winklers are a scalar multiplier which may be depth dependent depending on the cruise
- salinity are uncommon but are usually a linear fit