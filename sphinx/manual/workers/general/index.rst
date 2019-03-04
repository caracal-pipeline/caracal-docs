.. meerkathi documentation master file, created by
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



-------------------------------------
**data_path**
-------------------------------------

  *str*, *optional*

  where MeerKATHI (over-) writes HDF5 files and JSON info files downloaded by get_data below



-------------------------------------
**msdir**
-------------------------------------

  *str*, *optional*

  where MeerKATHI will write and expect to find measurement set (MS) files



-------------------------------------
**input**
-------------------------------------

  *str*, *optional*

  where MeerKATHI expects to find various input files (e.g., RFI flagging strategy files).



-------------------------------------
**output**
-------------------------------------

  *str*, *optional*

  where MeerKATHI writes output products



-------------------------------------
**prefix**
-------------------------------------

  *str*, *optional*

  Prefix for MeerKATHI output products



-------------------------------------
**init_pipeline**
-------------------------------------

  *bool*, *optional*

  Initialise pipeline by copying input files (meerkat specific; flagging strategies, beam model, etc.)
