.. caracal documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _transform:
 
==========================================
transform
==========================================
 
.. toctree::
   :maxdepth: 1
 
Split, average and/or calibrate the data.



.. _transform_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute the transform worker.



.. _transform_label_in:

--------------------------------------------------
**label_in**
--------------------------------------------------

  *str*, *optional*, *default = ' '*

  Label of the input dataset.



.. _transform_label_out:

--------------------------------------------------
**label_out**
--------------------------------------------------

  *str*, *optional*, *default = corr*

  Label of the output dataset.



.. _transform_rewind_flags:

--------------------------------------------------
**rewind_flags**
--------------------------------------------------

  Rewind flags to specified version.

  **enable**

    *bool*, *optional*, *default = False*

    Enable the 'rewind_flags' segment.

  **version**

    *str*, *optional*, *default = ' '*

    Flag version to restore. Note that all flag versions saved after this version will be deleted.



.. _transform_split_field:

--------------------------------------------------
**split_field**
--------------------------------------------------

  Make new MS of targets or calibrators.

  **enable**

    *bool*, *optional*, *default = True*

    Enable the 'split_field' segment.

  **field**

    *str*, *optional*, *default = target*

    Fields to be split off from the input MS. Options are (separately) 'target', 'calibrators', 'bpcal', 'gcal' and 'fcal'. Also valid is any combination of 'bpcal', 'gcal' and 'fcal' in a comma-separated string (e.g. 'bpcal, fcal').

  **time_average**

    *str*, *optional*, *default = ' '*

    Time averaging to apply to the data, in units of seconds. If this parameter is instead set to '' or '0s' then no time averaging is applied.

  **freq_average**

    *int*, *optional*, *default = 1*

    Frequency averaging to apply to the data, given as the number of channels per frequency bin. If this parameter is set to '', '0', or '1', then no frequency averaging is applied.

  **column**

    *str*, *optional*, *default = corrected*

    Column to be split, where the default is 'corrected'.

  **correlation**

    *str*, *optional*, *default = ' '*

    Select the correlations, e.g. 'XX', 'YY'. Setting this to '' means that all correlations are selected.

  **usewtspectrum**

    *bool*, *optional*, *default = True*

    Create a WEIGHT_SPECTRUM column in the output MS.

  **spw**

    *str*, *optional*, *default = ' '*

    Select spectral windows and channels, following the same syntax as for the 'mstransform' task in CASA. Setting this to '' means that all spectral windows and channels are selected.

  **otfcal**

    Apply on-the-fly (OTF) calibration.

    **enable**

      *bool*, *optional*, *default = False*

      Enable the 'otfcal' segment.

    **callib**

      *str*, *optional*, *default = ' '*

      Name of the callib file to be used, if user has their own.

    **label_cal**

      *str*, *optional*, *default = 1gc1*

      Label of the calibration tables to be used.



.. _transform_changecentre:

--------------------------------------------------
**changecentre**
--------------------------------------------------

  Change the phase centre.

  **enable**

    *bool*, *optional*, *default = False*

    Enable the 'changecentre' segment.

  **ra**

    *str*, *optional*, *default = 0h0m0.0s*

    J2000 RA of the new phase centre, in the format XXhXXmXX.XXs .

  **dec**

    *str*, *optional*, *default = 0d0m0.0s*

    J2000 Dec of the new phase centre, in the format XXdXXmXX.XXs .



.. _transform_obsinfo:

--------------------------------------------------
**obsinfo**
--------------------------------------------------

  Get observation information.

  **enable**

    *bool*, *optional*, *default = True*

    Enable the 'obsinfo' segment.

  **listobs**

    *bool*, *optional*, *default = True*

    Run the CASA 'listobs' task to get observation information.

  **summary_json**

    *bool*, *optional*, *default = True*

    Run the MSUtils summary function to get observation information written as a JSON file.



.. _transform_report:

--------------------------------------------------
**report**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  (Re)generate a full HTML report at the end of this segment.

