.. caracal documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _getdata:
 
==========================================
getdata
==========================================
 
.. toctree::
   :maxdepth: 1
 
Download and/or convert/unarchive data so that it is in the measurement set (MS) format for further processing.



.. _getdata_dataid:

--------------------------------------------------
**dataid**
--------------------------------------------------

  *list* *of str*

  Basename of MS. For MeerKAT data to be downloaded by CARACal, this should be the data ID of the observation.



.. _getdata_mvftoms:

--------------------------------------------------
**mvftoms**
--------------------------------------------------

  For MeerKAT HDFS files only -- Convert HDF5/MVF files in data_path (specified for the general worker) to MS files. The latter are written to msdir (also as specified for the general worker), and an MS.TAR file is created.

  **enable**

    *bool*, *optional*, *default = False*

    Enable the 'mvftoms' segment.

  **tar**

    *bool*, *optional*, *default = False*

    Create a tarball of the converted MS.

  **channel_range**

    *str*, *optional*, *default = all*

    Only extract channels in this range (0-based, inclusive; comma-separated string). It is also possible to specify 'all'.

  **full_poll**

    *bool*, *optional*, *default = False*

    Extract all four correlations instead of only the XX and YY correlations.



.. _getdata_untar:

--------------------------------------------------
**untar**
--------------------------------------------------

  Unarchive MS from an archive file.

  **enable**

    *bool*, *optional*, *default = False*

    Enable the 'untar' segment.

  **tar_options**

    *str*, *optional*, *default = -xvf*

    The tar options to pass to the 'tar' command.



.. _getdata_combine:

--------------------------------------------------
**combine**
--------------------------------------------------

  Virtually concatenate MSs and proceed with the combined MS.

  **enable**

    *bool*, *optional*, *default = False*

    Enable the 'combine' segment.

  **reset**

    *bool*, *optional*, *default = False*

    Delete concatenated MS if it exists. Otherwise, proceed with the existing MS.

  **tar**

    Create a tarball of the concatenated MS.

    **enable**

      *bool*, *optional*, *default = False*

      Enable the 'tar' segment.

    **tar_options**

      *str*, *optional*, *default = -cvf*

      The tar options to pass to the 'tar' command.

  **untar**

    Unarchive MS from an archive file.

    **enable**

      *bool*, *optional*, *default = False*

      Enable the 'untar' segment.

    **tar_options**

      *str*, *optional*, *default = -xvf*

      The tar options to pass to the 'tar' command.



.. _getdata_report:

--------------------------------------------------
**report**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  (Re)generate a full HTML report at the end of this segment.

