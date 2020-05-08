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
 
Split, avg and/or calibrate data



.. _transform_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute this worker



.. _transform_label_in:

--------------------------------------------------
**label_in**
--------------------------------------------------

  *str*, *optional*, *default = ' '*

  Label of the input dataset



.. _transform_label_out:

--------------------------------------------------
**label_out**
--------------------------------------------------

  *str*, *optional*, *default = corr*

  Label of the output dataset



.. _transform_rewind_flags:

--------------------------------------------------
**rewind_flags**
--------------------------------------------------

  Rewind flags to specified version.

  **enable**

    *bool*, *optional*, *default = False*

    enable this segement

  **version**

    *str*, *optional*, *default = auto*

    Flag version to restore. If 'auto' it will rewind to the version prefix_workername_before, where 'prefix' is set in the 'general' worker, and 'workername' is the name of this worker including the suffix '__N' if it is a repeated instance of this worker in the configuration file. Note that all flag versions saved after this version will be deleted.



.. _transform_split_field:

--------------------------------------------------
**split_field**
--------------------------------------------------

  Make new ms of targets or calibrators

  **enable**

    *bool*, *optional*, *default = True*

    Execute this section

  **field**

    *str*, *optional*, *default = target*

    Fields selected to be splitted - can be target, calibrators or bpcal, gcal, fcal in a comma separated string

  **time_average**

    *str*, *optional*, *default = ' '*

    Time averaging

  **freq_average**

    *int*, *optional*, *default = 1*

    Frequency averaging

  **column**

    *str*, *optional*, *default = corrected*

    Column to split, default is 'corrected'.

  **correlation**

    *str*, *optional*, *default = ' '*

    Select correlations

  **usewtspectrum**

    *bool*, *optional*, *default = True*

    Create a WEIGHT_SPECTRUM column in the output MS.

  **spw**

    *str*, *optional*, *default = ' '*

    Select spectral windows and channels

  **otfcal**

    Apply OTF calibration

    **enable**

      *bool*, *optional*, *default = False*

      Execute this section

    **callib**

      *str*, *optional*, *default = ' '*

      Name of callib file to be used, if user has their own

    **label_cal**

      *str*, *optional*, *default = 1gc1*

      Label of calibration tables to be used



.. _transform_changecentre:

--------------------------------------------------
**changecentre**
--------------------------------------------------

  changes the phase centre

  **enable**

    *bool*, *optional*, *default = False*

    Execute this section

  **ra**

    *str*, *optional*, *default = 0h0m0.0s*

    J2000 RA of new phase centre, format XXhXXmXX.XXs, default is empty string

  **dec**

    *str*, *optional*, *default = 0d0m0.0s*

    J2000 Dec of new phase centre, format XXdXXmXX.XXs, default is empty string



.. _transform_obsinfo:

--------------------------------------------------
**obsinfo**
--------------------------------------------------

  Get observation information

  **enable**

    *bool*, *optional*, *default = True*

    Execute this section

  **listobs**

    *bool*, *optional*, *default = True*

    Run CASA listobs

  **summary_json**

    *bool*, *optional*, *default = True*

    Run MSUtils function

