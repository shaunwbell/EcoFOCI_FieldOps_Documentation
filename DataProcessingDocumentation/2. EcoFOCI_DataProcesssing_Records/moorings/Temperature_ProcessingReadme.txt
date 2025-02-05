Workflow for Temperature Sensor Processing

This applies to SBE39, SBE56 and MTRs other units with temperature such as RCM/Seaguards, Seacats, MicroCats, etc will have similar temperature processing but will need to account for other datastreams

For Seabird instruments, use seabird software to download data record which will have engineering values already converted to temperatures
For MTRs which are developed in house, data records that are downloaded will be resistance values in hex that need to be converted and have the Steinhart-Hart equation and the calibration coefficients applied.

Walk through CSV+MetaData -> NetCDF JupyterNotebook.
- point to files
- point to metafiles
- choose depth
- choose time corrections
- interpolate/extrapolate/resample timebase to appropriate interval
- plot initial values for quick inspection
- trim deployment dates

QC Steps:
- look for good comparisons with field data points taken from CTD's
- look for good comparisons with other temperature timeseries at periods where water column is well mixed in relevant layers

Data Submission to ERDDAP
- untrimmed initial values go to initial_archive
- trimmed and qc'd values go to final_data_cf