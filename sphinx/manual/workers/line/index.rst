.. caracal documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _line:
 
==========================================
line
==========================================
 
.. toctree::
   :maxdepth: 1
 
Process visibilities for spectral line work and create line cubes and images.



.. _line_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute the image_line worker.



.. _line_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*, *default = corr*

  Label defining the name of the .MS files to be processed. The .MS file names are composed using the .MS names set by dataid in the get_data worker, followed by the target ID (one file per target), followed by this label. This is the format used by Caracal whenever it writes an .MS file to disk (e.g., in the split_target worker).



.. _line_line_name:

--------------------------------------------------
**line_name**
--------------------------------------------------

  *str*, *optional*, *default = HI*

  Suffix to be used for the name of the output files (data cubes etc).



.. _line_restfreq:

--------------------------------------------------
**restfreq**
--------------------------------------------------

  *str*, *optional*, *default = 1.420405752GHz*

  Spectral line rest frequency.



.. _line_rewind_flags:

--------------------------------------------------
**rewind_flags**
--------------------------------------------------

  Rewind flags of the input .MS file(s) to specified version. Note that this is not applied to .MS file(s) you might be running "transfer_apply_gains" on.

  **enable**

    *bool*, *optional*, *default = False*

    enable this segement

  **version**

    *str*, *optional*, *default = auto*

    Flag version to restore. This is applied to the .MS file(s) identified by "label" above. Set to "null" to skip this rewinding step. If 'auto' it will rewind to the version prefix_workername_before, where 'prefix' is set in the 'general' worker, and 'workername' is the name of this worker including the suffix '__N' if it is a repeated instance of this worker in the configuration file. Note that all flag versions saved after this version will be deleted.

  **mstransform_version**

    *str*, *optional*, *default = auto*

    Flag version to restore. This is applied to the .MS file(s) identified by "label" above plus the "_mst" suffix. Set to "null" to skip this rewind step. If 'auto' it will rewind to the version prefix_workername_before, where 'prefix' is set in the 'general' worker, and 'workername' is the name of this worker including the suffix '__N' if it is a repeated instance of this worker in the configuration file. Note that all flag versions saved after this version will be deleted.



.. _line_overwrite_flag_versions:

--------------------------------------------------
**overwrite_flag_versions**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  Allow Caracal to overwrite existing flag versions. Not recommended. Only enable this if you know what you are doing.



.. _line_subtractmodelcol:

--------------------------------------------------
**subtractmodelcol**
--------------------------------------------------

  Replace the CORRECTED_DATA column of the .MS file(s) with the difference CORRECTED_DATA - MODEL_DATA. This is useful for continuum subtraction as it subtracts the continuum clean model written to MODEL_DATA. WARNING! The CORRECTED_DATA column is overwritten. To undo this operation enable the addmodelcol segment in this worker.

  **enable**

    *bool*, *optional*, *default = True*

    Execute the segment subtractmodelcol.



.. _line_addmodelcol:

--------------------------------------------------
**addmodelcol**
--------------------------------------------------

  Replace the CORRECTED_DATA column of the .MS file(s) with the sum CORRECTED_DATA + MODEL_DATA. This is useful to undo the operation performed by subtractmodelcol in this worker. WARNING! The CORRECTED_DATA column is overwritten.

  **enable**

    *bool*, *optional*, *default = False*

    Execute the segment addmodelcol.



.. _line_mstransform:

--------------------------------------------------
**mstransform**
--------------------------------------------------

  Perform Doppler-tracking corrections and/or UVLIN continuum subtraction with CASA mstransform. For each input .MS file, this produces an output .MS file whose name is the same as that of the input .MS file plus the suffix "_mst".

  **enable**

    *bool*, *optional*, *default = True*

    Execute the segment mstransform.

  **column**

    *str*, *optional*, *default = corrected*

    Which column of the .MS file(s) to process.

  **doppler**

    Include the Doppler-tracking correction in the run of CASA mstransform.

    **enable**

      *bool*, *optional*, *default = True*

      Enable the Doppler correction section.

    **telescope**

      *{"askap", "atca", "gmrt", "meerkat", "vla", "wsrt"}*

      Name of the telescope used to take the data. This is used to set the telescope's geographical coordinates when calculating the Doppler correction. Default is 'meerkat'. Current options are askap, atca, gmrt, meerkat, vla, wsrt.

    **mode**

      *{"frequency"}*, *optional*, *default = frequency*

      Regridding mode (channel/velocity/frequency/channel_b). IMPORTANT! Currently only frequency mode is supported. Other modes will throw an error.

    **outframe**

      *{"", "topo", "geo", "lsrk", "lsrd", "bary", "galacto", "lgroup", "cmb", "source"}*, *optional*, *default = bary*

      Output reference frame. Current options are '', topo, geo, lsrk, lsrd, bary, galacto, lgroup, cmb, source.

    **veltype**

      *{"radio", "optical"}*, *optional*, *default = radio*

      Velocity used when regridding if mode = velocity. Current options are radio, optical.

    **outchangrid**

      *str*, *optional*, *default = auto*

      Output channel grid for Doppler correction. Default is 'auto', and the pipeline will calculate the appropriate channel grid. If not 'auto' it must be in the format 'nchan,chan0,chanw' where nchan is an integer, and chan0 and chanw must include units appropriate for the chosen mode (see parameter 'mode' above).

  **uvlin**

    Include UVLIN-like continuum subtraction in the run of CASA mstransform.

    **enable**

      *bool*, *optional*, *default = True*

      Enable the UVLIN section.

    **fitspw**

      *str*, *optional*, *default = ' '*

      Selection of line-free channels using CASA syntax (e.g. '0:0~100;150:300'). If set to null, a fit to all unflagges visibilities will be performed.

    **fitorder**

      *int*, *optional*, *default = 1*

      Polynomial order of the continuum fit.

  **obsinfo**

    *bool*, *optional*, *default = True*

    Create obsinfo.txt and obsinfo.json of the .MS file(s) created by CASA mstransform.



.. _line_flag_mst_errors:

--------------------------------------------------
**flag_mst_errors**
--------------------------------------------------

  Run AOFlagger to flag any faulty visibilities produced by CASA mstransform.

  **enable**

    *bool*, *optional*, *default = False*

    Execute segment flag_mst_errors.

  **strategy**

    *str*, *optional*, *default = postmst.rfis*

    AOFlagger strategy file



.. _line_sunblocker:

--------------------------------------------------
**sunblocker**
--------------------------------------------------

  Use sunblocker to grid the visibilities and flag UV cells affected by solar RFI. See description of sunblocker on github repository gigjozsa/sunblocker in method phazer of module sunblocker.py.

  **enable**

    *bool*, *optional*, *default = False*

    Execute segment sunblocker.

  **use_mstransform**

    *bool*, *optional*, *default = True*

    Run sunblocker on the .MS file(s) produced by the mstransform section of this worker instead of the input .MS file(s).

  **imsize**

    *int*, *optional*, *default = 900*

    Image size (pixels). Use the same as in the make_cube section. This is used to set up the gridding of the visibilities.

  **cell**

    *float*, *optional*, *default = 2.*

    Pixel size (arcsec). Use the same as in the make_cube section. This is used to set up the gridding of the visibilities.

  **threshold**

    *float*, *optional*, *default = 4.*

    Flag UV cells whose visibility deviates by more than this threshold from the average visibility on the UV plane. The threshold is in units of the rms dispersion of all visibilities.

  **vampirisms**

    *bool*, *optional*, *default = False*

    Apply the flags to data taken during day time only. Note that all data are used when calculating which UV cells where to flag.

  **uvmin**

    *float*, *optional*, *default = 0.*

    Minimum uvdistance to be analysed (in wavelengths).

  **uvmax**

    *float*, *optional*, *default = 2000*

    Maximum uvdistance to be analysed (in wavelengths).



.. _line_make_cube:

--------------------------------------------------
**make_cube**
--------------------------------------------------

  Make a line cube using either WSclean + SoFiA (optional for clean masks) or CASA Clean.

  **enable**

    *bool*, *optional*, *default = True*

    Execute segment make_cube.

  **image_with**

    *{"wsclean", "casa"}*, *optional*, *default = wsclean*

    Choose whether to image with WSclean + SoFiA ('wsclean') or with CASA Clean ('casa').

  **use_mstransform**

    *bool*, *optional*, *default = True*

    Image the .MS file(s) produced by the mstransform section of this worker instead of the input .MS file(s).

  **pol**

    *str*, *optional*, *default = I*

    Polarizations in output cube (I,Q,U,V,XX,YY,XY,YX,RR,LL,RL,LR and combinations).

  **spwid**

    *int*, *optional*, *default = 0*

    Spectral window to use.

  **nchans**

    *int*, *optional*, *default = 0*

    Number of channels of the line cube, 0 means all channels.

  **firstchan**

    *int*, *optional*, *default = 0*

    First channel of the line cube.

  **binchans**

    *int*, *optional*, *default = 1*

    Integer binning of channels.

  **npix**

    *seq*, *optional*, *default = 900 , 900*

    Image size in pixels. List of integers (width and height) or a single integer for square images.

  **cell**

    *float*, *optional*, *default = 2*

    Pixel size. The default unit is arcsec, but other units can be specificied, e.g., 'scale 20asec'.

  **padding**

    *float*, *optional*, *default = 1.2*

    Images have initial size padding\*npix, and are later trimmed to npix.

  **weight**

    *{"natural", "uniform", "briggs"}*, *optional*, *default = briggs*

    Weightmode can be natural, uniform, briggs. When using Briggs weighting, the additional robust parameter has to be specified.

  **robust**

    *float*, *optional*, *default = 0*

    Robust parameter in case of Briggs weighting.

  **taper**

    *float*, *optional*, *default = 0*

    Gaussian taper FWHM in arcsec. Zero means no tapering.

  **niter**

    *int*, *optional*, *default = 1000000*

    Maximum number of clean iterations to perform.

  **gain**

    *float*, *optional*, *default = 0.1*

    Fraction of the peak that is cleaned in each minor iteration.

  **wscl_mgain**

    *float*, *optional*, *default = 1.0*

    WSclean gain for major iterations, i.e., maximum fraction of the image peak that is cleaned in each major iteration. A value of 1 means that all cleaning happens in the image plane and no major cycle is performed.

  **wscl_sofia_niter**

    *int*, *optional*, *default = 2*

    Maximum number of WSclean + SoFiA iterations. The initial cleaning is done with WSclean automasking or with a user clean mask. Subsequent iterations use a SoFiA clean mask. A value of 1 means that WSclean is only executed once and SoFiA is not used.

  **wscl_sofia_converge**

    *float*, *optional*, *default = 1.1*

    Stop the WSclean + SoFiA iterations if the cube RMS has dropped by a factor < wscl_sofia_converge when comparing the last two iterations (considering only channels that were cleaned). If set to 0 then the maximum number of iterations is performed regardless of the noise change.

  **wscl_keep_final_products_only**

    *bool*, *optional*, *default = False*

    If set to true it deletes WSclean + Sofia intermediate cubes from the output directory, if set to false it keeps all the cubes of the WSclean + SoFiA iterations.

  **wscl_user_clean_mask**

    *str*, *optional*, *default = ' '*

    WSclean user clean mask for first WSclean + SoFiA iteration (give filename, to be located in the output/masking folder).

  **wscl_auto_mask**

    *float*, *optional*, *default = 10*

    Used only during the first WSclean iteration. Clean blindly down to a threshold given by this parameter (in  units of the noise), then clean again the already cleaned pixels down to the parameter wscl_auto_threshold.

  **wscl_auto_threshold**

    *float*, *optional*, *default = 0.5*

    WSclean cleaning threshold in units of the noise.

  **wscl_make_cube**

    *bool*, *optional*, *default = True*

    If set to true the output of WSclean is a data cube, if set to false the output is one .FITS image per spectral channel.

  **wscl_no_update_mod**

    *bool*, *optional*, *default = True*

    If set to true, WSclean will not store the line clean model in MODEL_DATA.

  **wscl_multi_scale**

    *bool*, *optional*, *default = False*

    Switch on WSclean multiscale cleaning.

  **wscl_multi_scale_scales**

    *list* *of int*, *optional*, *default = 0, 10, 20, 30*

    List of scales of WSclean multiscale in units of pixels. Only used is wscl_multi_scale is set to True.

  **wscl_multi_scale_bias**

    *float*, *optional*, *default = 0.6*

    Parameter to set the bias towards larger scales during multi-scale cleaning. A lower bias will give preference to larger scales.

  **casa_threshold**

    *str*, *optional*, *default = 10mJy*

    Flux level to stop CASA cleaning. It must include units, e.g. '1.0mJy'.

  **casa_port2fits**

    *bool*, *optional*, *default = False*

    Port CASA output to fits files.



.. _line_remove_stokes_axis:

--------------------------------------------------
**remove_stokes_axis**
--------------------------------------------------

  Remove the Stokes axis from the line cube.

  **enable**

    *bool*, *optional*, *default = False*

    Execute segment remove_stokes_axis.



.. _line_pb_cube:

--------------------------------------------------
**pb_cube**
--------------------------------------------------

  Make a primary beam cube.

  **enable**

    *bool*, *optional*, *default = False*

    Execute segment pb_cube.

  **apply_pb**

    *bool*, *optional*, *default = False*

    Whether to apply the primary beam correction to the image cube.



.. _line_freq_to_vel:

--------------------------------------------------
**freq_to_vel**
--------------------------------------------------

  Convert the spectral axis' header keys of the line cube from frequency to velocity in the radio definition, v=c(1-obsfreq/restfreq). No change of spectra reference frame is performed.

  **enable**

    *bool*, *optional*, *default = False*

    Execute segment freq_to_vel.

  **reverse**

    *bool*, *optional*, *default = False*

    Perform the inverse transformation and change the cube 3rd axis from radio velocity to frequency.



.. _line_sofia:

--------------------------------------------------
**sofia**
--------------------------------------------------

  Run SoFiA source finder to produce a detection mask, moment images and catalogues.

  **enable**

    *bool*, *optional*, *default = True*

    Execute segment sofia.

  **flag**

    *bool*, *optional*, *default = False*

    Use flag regions?

  **flagregion**

    *list* *of int*, *optional*, *default = 0, 0, 0, 0, 0, 0*

    Pixel/channel range(s) to be flagged prior to source finding. Format is [[x1, x2, y1, y2, z1, z2], ...].

  **rmsMode**

    *str*, *optional*, *default = mad*

    Method to determine rms ('mad' for using median absolute deviation, 'std' for using standard deviation, 'negative' for using Gaussian fit to negative voxels).

  **threshold**

    *float*, *optional*, *default = 4.0*

    SoFiA source finding threshold.

  **merge**

    *bool*, *optional*, *default = False*

    Merge pixels detected by any of SoFiA source finding algorithms into objects. If turned on, pixels with a separation of less than mergeX pixels in the X direction, mergeY pixels in Y direction, and mergeZ channels in Z direction will be merged and identified as a single object in the mask. Objects whose extent is smaller than minSizeX, minSizeY or minSizeZ will be removed from the mask.

  **mergeX**

    *int*, *optional*, *default = 2*

    Merging radius (in pixels) in the X direction (RA axis).

  **mergeY**

    *int*, *optional*, *default = 2*

    Merging radius (in pixels) in the Y direction (Dec axis).

  **mergeZ**

    *int*, *optional*, *default = 3*

    Merging radius (in channels) in Z direction (spectral axis).

  **minSizeX**

    *int*, *optional*, *default = 3*

    Minimum size (in pixels) in the X direction (RA axis).

  **minSizeY**

    *int*, *optional*, *default = 3*

    Minimum size (in pixels) in  the Y direction (Dec axis).

  **minSizeZ**

    *int*, *optional*, *default = 3*

    Minimum size (in channels) in the Z direction (spectral axis).

  **do_cubelets**

    *bool*, *optional*, *default = True*

    Create a cubelet for each detected emission-line object.

  **do_mom0**

    *bool*, *optional*, *default = True*

    Create a moment-0 image of the field.

  **do_mom1**

    *bool*, *optional*, *default = True*

    Create a moment-1 image of the field.



.. _line_sharpener:

--------------------------------------------------
**sharpener**
--------------------------------------------------

  Run sharpener to extract and plot the spectra of all continuum sources brighter than a given threshold.

  **enable**

    *bool*, *optional*, *default = False*

    Execute segment sharpener.

  **catalog**

    *{"NVSS", "PYBDSF"}*, *optional*, *default = PYBDSF*

    Type of catalog to use (PYBDSF/NVSS).

  **channels_per_plot**

    *int*, *optional*, *default = 50*

    Number of channels to plot per detail plot.

  **thresh**

    *float*, *optional*, *default = 20*

    Threshold to select sources in online catalogs (mJy).

  **width**

    *str*, *optional*, *default = 1.0d*

    Field of view of output catalog (degrees).

  **label**

    *str*, *optional*, *default = ' '*

    Prefix label of plot names and titles.

