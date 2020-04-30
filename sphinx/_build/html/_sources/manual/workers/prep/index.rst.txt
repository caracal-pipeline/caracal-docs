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

  Executes the data preparation step.



.. _prep_label_in:

--------------------------------------------------
**label_in**
--------------------------------------------------

  *str*

  If this label is an empty string this worker operates on the input .MS file(s) given in the getdata worker. If the label is not an empty string it is added to the input .MS file(s) name given in the getdata worker to define the name of the .MS file(s) to work on. These are <input>_<label>.ms if 'field' (see below) is set to 'calibrators', or <input>-<target>_<label>.ms if 'field' is set to 'target' (one .MS file for each target in the input .MS).



.. _prep_field:

--------------------------------------------------
**field**
--------------------------------------------------

  *{"target", "calibrators"}*, *optional*, *default = calibrators*

  In combination with a non-empty 'label_in' (see above), 'field' defines which .MS file(s) to work on. This parameter is ignored if 'label_in' is empty.



.. _prep_fixvis:

--------------------------------------------------
**fixvis**
--------------------------------------------------

  Fixes the UVW coordinates through the CASA task fixvis.

  **enable**

    *bool*, *optional*, *default = False*

    Enable execution of fixvis.



.. _prep_clear_cal:

--------------------------------------------------
**clear_cal**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  Clears out calibrated data and resets previous predicted model



.. _prep_manage_flags:

--------------------------------------------------
**manage_flags**
--------------------------------------------------

  Manage flags

  **enable**

    *bool*, *optional*, *default = True*

    Enable this segment

  **mode**

    *{"save_legacy_flags", "restore"}*, *optional*, *default = save_legacy_flags*

    Manage flag mode. If "save_legacy_flags" save the current FLAG column as a "caracal_legacy" flag version (if that already exists, "overwrite_legacy_flags" below allows you to overwrite it, but think twice). If "restore" restore flags from the flag version specified by "version" below, and delete all flag versions created after that version.

  **version**

    *str*, *optional*, *default = caracal_legacy*

    Flag version to restore. Note that all flag versions saved after this version will be deleted.

  **overwrite_legacy_flags**

    *bool*, *optional*, *default = False*

    If "mode" above is "save_legacy_flags" but the "caracal_legacy" flag version already exists, allow Caracal to overwrite it. Think twice!



.. _prep_spectral_weights:

--------------------------------------------------
**spectral_weights**
--------------------------------------------------

  How to initialize spectral weights

  **enable**

    *bool*, *optional*, *default = False*

    Enable this segment

  **mode**

    *{"uniform", "estimate", "delete"}*, *optional*, *default = uniform*

    uniform: Set all weights to unity. estimate: Estimate spectral weights from frequency-dependent SEFD/Tsys/Noise values, Also see 'estimate' segment of this section. delete: Delete WEIGHT_SPECTRUM column if it exists.

  **estimate**

    Estimate spectral weights from frequency-dependent SEFD/Tsys/Noise values

    **stats_data**

      *str*, *optional*, *default = use_package_meerkat_spec*

      File with SEFD/Tsys/Noise data. If data is from MeerKAT telescope, you can specify 'use_package_meerkat_spec' to use package data.

    **weight_columns**

      *list* *of str*, *optional*, *default = WEIGHT, WEIGHT_SPECTRUM*

      column names

    **noise_columns**

      *list* *of str*, *optional*, *default = SIGMA, SIGMA_SPECTRUM*

      column names for noise

    **write_to_ms**

      *bool*, *optional*, *default = True*

      write columns to file

