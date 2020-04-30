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

    *str*, *optional*, *default = INSERT_FLAG_VERSION_TO_BE_RESTORED*

    Flag version to restore. Note that all flag versions saved after this version will be deleted.



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

    **apply_delay_cal**

      Apply the delay correction calibration table to specified fields via the CASA applycal task.

      **enable**

        *bool*, *optional*, *default = True*

        Executes application of delay correction calibration table.

      **field**

        *list* *of str*

        Field to select in the delay correction calibration table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'bpcal'.

    **apply_bp_cal**

      Apply the bandpass table to specified fields via the CASA applycal task.

      **enable**

        *bool*, *optional*, *default = True*

        Executes application of bandpass table.

      **field**

        *list* *of str*

        Field to select in the bandpass table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'bpcal'.

    **apply_gain_cal_gain**

      Apply the gain calibration table to specified fields via the CASA applycal task.

      **enable**

        *bool*, *optional*, *default = False*

        Executes application of gain calibration table.

      **field**

        *list* *of str*

        Field to select in the gain calibration table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'gcal'.

    **apply_transfer_fluxscale**

      Apply the fluxscale table to specified fields via the CASA applycal task.

      **enable**

        *bool*, *optional*, *default = True*

        Executes application of fluxscale table.

      **field**

        *list* *of str*, *optional*, *default = gcal*

        Field to select in the fluxscale table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'gcal'.



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

