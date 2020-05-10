.. caracal documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _prep:
 
==========================================
prep
==========================================
 
.. toctree::
   :maxdepth: 1
 
Prepare the data for calibration and imaging.



.. _prep_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute the prep worker (i.e. the  data-preparation step).



.. _prep_label_in:

--------------------------------------------------
**label_in**
--------------------------------------------------

  *str*

  If this label is an empty string this worker operates on the input .MS file(s) given in the getdata worker. If the label is not an empty string then it is added to the input .MS file(s) name (specified for the getdata worker) to define the name of the .MS file(s) to work on. These are named <input>_<label>.ms if 'field' (see below) is set to 'calibrators', or <input>-<target>_<label>.ms if 'field' is set to 'target' (with one .MS file for each target in the input .MS).



.. _prep_field:

--------------------------------------------------
**field**
--------------------------------------------------

  *{"target", "calibrators"}*, *optional*, *default = calibrators*

  In combination with a non-empty 'label_in' (see above), 'field' defines which .MS file(s) to work on. This parameter is ignored if 'label_in' is empty. Options are 'target' and 'calibrators'.



.. _prep_fixvis:

--------------------------------------------------
**fixvis**
--------------------------------------------------

  Fix the UVW coordinates through the CASA task 'fixvis'.

  **enable**

    *bool*, *optional*, *default = False*

    Enable the 'fixvis' segment.



.. _prep_clear_cal:

--------------------------------------------------
**clear_cal**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  Clear out calibrated data and reset the previous predicted model.



.. _prep_manage_flags:

--------------------------------------------------
**manage_flags**
--------------------------------------------------

  Manage flags.

  **enable**

    *bool*, *optional*, *default = True*

    Enable the 'manage_flags' segment.

  **mode**

    *{"legacy", "restore"}*, *optional*, *default = legacy*

    Mode for managing flags. If set to 'legacy', save the current FLAG column as a 'caracal_legacy' flag version if a flag version with that name does not exisy yet; else restore the 'caracal_legacy' flag version and delete all flag versions created after it. If set to 'restore', restore flags from the flag version specified by 'version' below, and delete all flag versions created after that version.

  **version**

    *str*, *optional*, *default = auto*

    Name of the flag version to restore. If set to 'auto', rewind to the version prefix_workername_before, where 'prefix' is set in the 'general' worker, and 'workername' is the name of this worker including the suffix '__X' if it is a repeated instance of this worker in the configuration file. Note that all flag versions saved after this version will be deleted.



.. _prep_spectral_weights:

--------------------------------------------------
**spectral_weights**
--------------------------------------------------

  How to initialize spectral weights.

  **enable**

    *bool*, *optional*, *default = False*

    Enable the 'spectral_weights' segment.

  **mode**

    *{"uniform", "estimate", "delete"}*, *optional*, *default = uniform*

    Mode for spectral weights. Options are 'uniform' (set all weights to unity), 'estimate' (estimate spectral weights from frequency-dependent SEFD/Tsys/Noise values, and see 'estimate' segment of this section), and 'delete' (delete WEIGHT_SPECTRUM column if it exists).

  **estimate**

    Estimate spectral weights from frequency-dependent SEFD/Tsys/Noise values.

    **stats_data**

      *str*, *optional*, *default = use_package_meerkat_spec*

      File with SEFD/Tsys/Noise data. If data is from the MeerKAT telescope, you can specify 'use_package_meerkat_spec' to use package data.

    **weight_columns**

      *list* *of str*, *optional*, *default = WEIGHT, WEIGHT_SPECTRUM*

      Column names for spectral weights.

    **noise_columns**

      *list* *of str*, *optional*, *default = SIGMA, SIGMA_SPECTRUM*

      Column names for noise values.

    **write_to_ms**

      *bool*, *optional*, *default = True*

      Write columns to file.



.. _prep_report:

--------------------------------------------------
**report**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  (Re)generate a full HTML report at the end of this segment.

