.. caracal documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
=========================
Prepare pipeline and data
=========================
 
.. toctree::
   :maxdepth: 1

**[relevant workers:** :ref:`general`, :ref:`getdata`, :ref:`obsconf`, :ref:`prep`\ **]**

--------------------------------
Directories and input file names
--------------------------------
 
A run of Caracal must always start by setting up a number of directory and file
names. This is done through the :ref:`general` and :ref:`getdata` workers.

In the :ref:`general` worker users give:

* if necessary, the *data_path* directory where to find the files that should be converted to .MS
  format (:ref:`general: data_path <general_data_path>`);
* the *msdir* directory where to find/write .MS files (:ref:`general: msdir <general_msdir>`);
* the *output* directory where to write all output data products (:ref:`general: output <general_output>`);
* the *input* directory where to find various input files, such as AOflagger strategies etc.
  (:ref:`general: input <general_input>`);
* the prefix for the output data products (:ref:`general: prefix <general_prefix>`).

If they do not exist yet, the above directories can be created by setting
:ref:`general: init_pipeline <general_init_pipeline>` to *true*. This also copies
files from the caracal/data/meerkat_files directory to the *input* directory set above.

In the :ref:`getdata` worker users give the name of the .MS files to be processed
(:ref:`getdata: dataid <getdata_dataid>`). Furthermore, the following optional steps are available:

* convert from HDF5/MVF format to .MS (:ref:`getdata: mvftoms <getdata_mvftoms>`);
  this step includes the following additional conversion options:

  + create a .MS.TAR file,
  + convert only visibilities in a selected channel range,
  + discard cross-polarisation products;

* untar an existing .MS.TAR file (:ref:`getdata: untar <getdata_untar>`);
* virtually concatenate all .MS input files (:ref:`getdata: combine <getdata_combine>`);
  optionally users can delete an existing concatenate file and tar/untar the concatenated file.

--------
Metadata
--------

Finally, before starting the actual data processing users need to provide some
info about the content of the input .MS files through the :ref:`obsconf` worker
(e.g., target and calibrators name, channelisation, etc.). In principle, this can be done
by editing the relevant parameters of this worker:

* :ref:`obsconf: target <obsconf_target>`
* :ref:`obsconf: bpcal <obsconf_bpcal>`
* :ref:`obsconf: fcal <obsconf_fcal>`
* :ref:`obsconf: gcal <obsconf_gcal>`
* :ref:`obsconf: reference_antenna <obsconf_reference_antenna>`

In fact, Caracal can automatically extract
most of these info from the .MS files themselves. To do so users should enable the
:ref:`obsconf: obsinfo <obsconf_obsinfo>` parameter. This writes a .JSON and a .TXT file to disc. Once
the .JSON file is on disc, parameters set to *auto* (or in some cases to 0) in the :ref:`obsconf`
worker will be automatically read from that file.

Note that the reference antenna information is often missing from the metadata. In those
cases, users should carefully select a good reference antenna for calibration and set it
with the :ref:`obsconf: reference_antenna <obsconf_reference_antenna>`
parameter.

**[missing from this page: vampirisms]**
