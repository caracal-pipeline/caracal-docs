.. caracal documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _general:
 
==========================================
general
==========================================
 
.. toctree::
   :maxdepth: 1
 
General pipeline information, data IDs, prefixes for output



.. _general_title:

--------------------------------------------------
**title**
--------------------------------------------------

  *str*, *optional*, *default = ' '*

  an optional, descriptive, project title



.. _general_data_path:

--------------------------------------------------
**data_path**
--------------------------------------------------

  *str*, *optional*, *default = ' '*

  where CARACal (over-) writes HDF5 files and JSON info files downloaded by get_data below



.. _general_msdir:

--------------------------------------------------
**msdir**
--------------------------------------------------

  *str*, *optional*, *default = msdir*

  where CARACal will write and expect to find measurement set (MS) files



.. _general_input:

--------------------------------------------------
**input**
--------------------------------------------------

  *str*, *optional*, *default = input*

  where CARACal expects to find various input files (e.g., RFI flagging strategy files).



.. _general_output:

--------------------------------------------------
**output**
--------------------------------------------------

  *str*, *optional*, *default = output*

  where CARACal writes output products



.. _general_prefix:

--------------------------------------------------
**prefix**
--------------------------------------------------

  *str*, *optional*, *default = caracal*

  Prefix for CARACal output products



.. _general_init_pipeline:

--------------------------------------------------
**init_pipeline**
--------------------------------------------------

  *bool*, *optional*, *default = True*

  Initialise pipeline by copying input files (meerkat specific; flagging strategies, beam model, etc.)



.. _general_init_notebooks:

--------------------------------------------------
**init_notebooks**
--------------------------------------------------

  *list* *of str*, *optional*, *default = std-progress-report*

  Install standard radiopadre notebooks, given by list of basenames

