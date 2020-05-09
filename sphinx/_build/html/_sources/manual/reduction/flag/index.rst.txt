.. caracal documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
==========================
Flagging and flag versions
==========================
 
.. toctree::
   :maxdepth: 1
 
**[relevant workers:** :ref:`flag`, :ref:`crosscal`, :ref:`selfcal`, :ref:`line`\ **]**

Several Caracal workers can flag visibilities. The most obvious one is the :ref:`flag`
worker. However, the :ref:`crosscal` and :ref:`selfcal` workers can also flag based on
both  gains and visibilities; and the :ref:`line` worker can flag solar RFI and potential
continuum subtraction errors.

Users can navigate through the different flagging steps thanks to the flag versions saved
by Caracal to disk. Most workers can indeed rewind the flags to a specified version, which
allows users to correct errors or repeat certain processing steps without too much effort.

Here we explain the Caracal's management of flag versions, and describe the :ref:`flag`
worker. The flagging done by the other workers mentioned above is described in other
paper of the Data Reduction section of this Caracal manual.

---------------------------
Management of flag versions
---------------------------

General principle.

---------------
The flag worker
---------------

The :ref:`flag` worker can run on the input .MS files or on .MS files created by
Caracal at various stages of the pipeline (e.g., by the :ref:`transform` worker).
In the latter case the name of the .MS files to be flagged is based on that of the input
.MS files, with a label added before the extension. Users can set the label with the
:ref:`flag: label_in <flag_label_in>` parameter in this worker.

The :ref:`flag` worker allows users to flag the data in a variety of ways. Unless
otherwise stated below, flagging is done with the CASA task FLAGDATA. Follow the links
below for a detailed documentation of the individual flagging modes.


* Unflag all data.
* Flag on autocorrelations to catch antennas with obvious problems using the custom
  program POLITSIYAKAT (:ref:`flag: flag_autopowerspec <flag_flag_autopowerspec>`).
  Individual scans are compared to the median of all scans per field and channel; and
  individual antennas are compared to the median of all antennas per scan, field and channel.
  Both methods have their own flagging threshold, which users can tune. Users can also set
  which column and which fields to flag.
* Flag all autocorrelations (:ref:`flag: flag_autocorr <flag_flag_autocorr>`).
* Flag specific portions of the beginning and/or end of each scan
  (:ref:`flag: flag_quack <flag_flag_quack>`).
  As in the CASA task FLAGDATA, users can set the time interval that should be flagged
  and the quackmode.
* Flag shadowed antennas (:ref:`flag: flag_shadow <flag_flag_shadow>`).
  Users can tune the amount of shadowing allowed before flagging an antenna.
  For observations obtained with a MeerKAT subarray it is possible to include offline
  antennas in the shadowing calculation.
* Flag selected channel ranges (:ref:`flag: flag_spw <flag_flag_spw>`).
* Flag selected time ranges (:ref:`flag: flag_time <flag_flag_time>`).
* Flag selected antennas (:ref:`flag: flag_antennas <flag_flag_antennas>`).
  Within this task, users can limit the flagging of selected antennas to a
  selected timerange.
* Flag selected scans (:ref:`flag: flag_scan <flag_flag_scan>`).
* Flag according to a static mask of bad frequency ranges using the custom program
  RFIMASKER (:ref:`flag: flag_mask <flag_flag_mask>`). The mask file should
  be located in the *input* directory set by :ref:`general: input <general_input>`.
  Users can decide to limit the flagging to a selected UV range. This could be useful
  to flag short baselines only.
* Flag RFI choosing between the available algorithms and strategies (:ref:`flag: flag_rfi <flag_flag_rfi>`).
  Possible choices include AOFlagger, Tricolour, CASA tfcrop. The requested
  AOFlagger or tricolour strategy file should be located in the *input* directory set by
  :ref:`general: input <general_input>`.
  Caracal comes with a number of strategy files, which are located in the
  caracal/data/meerkat_files directory and are copied to the *input* directory by the
  :ref:`general` worker. However, users can copy their own strategy file to the same
  *input* directory and use it within Caracal.

Finally, a summary of the flags can be obtained with :ref:`flag: summary <flag_summary>`.
The summary is available at the relevant log file (see :ref:`products`).
