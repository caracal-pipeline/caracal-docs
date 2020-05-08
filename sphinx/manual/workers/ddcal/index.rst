.. caracal documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _ddcal:
 
==========================================
ddcal
==========================================
 
.. toctree::
   :maxdepth: 1
 
Perform direction dependent calibration on the data



.. _ddcal_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Carry out DD-calibration



.. _ddcal_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*, *default = DD*

  Label of the .MS files to process.



.. _ddcal_use_pb:

--------------------------------------------------
**use_pb**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  Enable primary beam usage in making the dd-corrected ddfacet image (only MeerKAT for the moment). EXPERIMENTAL.



.. _ddcal_image_dd:

--------------------------------------------------
**image_dd**
--------------------------------------------------

  Imaging parameters for DD calibration loop with DDFacet

  **enable**

    *bool*, *optional*, *default = True*

    Execute this section.

  **npix**

    *int*, *optional*, *default = 8000*

    Number of pixels in the image.

  **use_mask**

    *bool*, *optional*, *default = True*

    Enable masks for DDfacet initial imaging.

  **mask_sigma**

    *float*, *optional*, *default = 10.0*

    The number of standard deviations to use when clipping the initial image for masking.

  **mask_boxes**

    *int*, *optional*, *default = 9*

    Will divide initial image (for making the mask) into this number of boxes, then perform sigma clipping in each of these boxes.

  **mask_iters**

    *int*, *optional*, *default = 20*

    The number of iterations to perform sigma clipping on the image for masking, or 0 to clip until convergence is achieved.

  **mask_overlap**

    *float*, *optional*, *default = 0.3*

    Overlap region for the boxes. As a fraction of -nb/--boxes

  **mask_tolerance**

    *float*, *optional*, *default = 0.75*

    Tolerance for dilating the mask. Will stop dilating if percentage difference between dilations is smaller than this value.

  **cell**

    *float*, *optional*, *default = 1.3*

    Pixel size in arcsec.

  **facets_nfacets**

    *int*, *optional*, *default = 24*

    Number of facets to use, same as Facets-NFacets.

  **weight_column**

    *{"WEIGHT_SPECTRUM", "WEIGHT", "IMAGING_WEIGHT"}*, *optional*, *default = WEIGHT*

    Read data weights from specified column. Use WEIGHT_SPECTRUM or WEIGHT, more rarely IMAGING_WEIGHT.

  **weight_mode**

    *{"Natural", "Uniform", "Robust", "Briggs"}*, *optional*, *default = Briggs*

    UV weighting mode

  **weight_robust**

    *float*, *optional*, *default = -0.4*

    Briggs robustness parameter, from -2 (more uniform) to 2 (more natural)

  **deconv_maxminoriter**

    *int*, *optional*, *default = 100000*

    Number of clean iterations

  **freq_nband**

    *int*, *optional*, *default = 10*

    N Number of image bands for gridding.

  **freq_ndegridband**

    *int*, *optional*, *default = 15*

    N Number of image bands for degridding. 0 means degrid each channel.

  **deconv_rmsfactor**

    *float*, *optional*, *default = 0.0*

    X Set minor cycle stopping threshold to X\*{residual RMS} (HMP, Hogbom).

  **deconv_peakfactor**

    *float*, *optional*, *default = 0.25*

    X Set minor cycle stopping threshold to X\*{peak residual} (HMP, Hogbom).

  **deconv_mode**

    *{"HMP", "Hogbom", "SSD", "GAClean"}*, *optional*, *default = Hogbom*

    Deconvolution algorithm.

  **deconv_gain**

    *float*, *optional*, *default = 0.1*

    GAIN Loop gain (HMP, Hogbom).

  **deconv_fluxthreshold**

    *float*, *optional*, *default = 1.0e-6*

    Jy Absolute flux threshold at which deconvolution is stopped (HMP, Hogbom).

  **deconv_allownegative**

    *bool*, *optional*, *default = True*

    Allow negative components (HMP, Hogbom).

  **hogbom_polyfitorder**

    *int*, *optional*, *default = 6*

    HOGBOM_POLYFITORDER polynomial order for frequency fitting

  **parallel_ncpu**

    *int*, *optional*, *default = 0*

    Number of processes / threads to use in parallel mode. 0 - all available. 1 - disable parallelism

  **predict_colname**

    *str*, *optional*, *default = MODEL_DATA*

    MS column to write predict to. Can be left empty to disable

  **log_memory**

    *bool*, *optional*, *default = True*

    log memory use

  **cache_reset**

    *bool*, *optional*, *default = True*

    Reset all caches (including PSF and dirty image). Change from default at your own risk.

  **log_boring**

    *bool*, *optional*, *default = True*

    Enable progress bars and other pretty console output. Doesn't seem to work.

  **data_colname**

    *str*, *optional*, *default = CORRECTED_DATA*

    Data column to use for initial imaging. Defaults to 'CORRECTED_DATA', the assumption being that self-calibration has already been done on the measurement set.

  **data_chunkhours**

    *float*, *optional*, *default = 0.05*

    Chunk data into time bins of x hours to conserve memory

  **output_mode**

    *{"Dirty", "Clean", "Predict", "PSF"}*, *optional*, *default = Clean*

    Output mode



.. _ddcal_calibrate_dd:

--------------------------------------------------
**calibrate_dd**
--------------------------------------------------

  Direction dependent calibration parameters

  **enable**

    *bool*, *optional*, *default = True*

    Execute this section.

  **sigma**

    *float*, *optional*, *default = 4.5*

    Threshold to use in detecting outlier regions in images by using CatDagger. 4.5 is a good value (also default), but may need a lower value for some images.

  **min_dist_from_phcentre**

    *int*, *optional*, *default = 1300*

    Number of pixels (radius) around the centre of the image in which sources will not be tagged. Default kept at 1300 (roughly 30').

  **dist_ncpu**

    *int*, *optional*, *default = 1*

    Number of cpus

  **de_sources_mode**

    *str*, *optional*, *default = manual*

    Mode in which dE sources are tagged. 'auto' uses catdagger, while in 'manual' mode, one needs to give a list of sources. Use 'auto' with caution and at your own risk.

  **de_target_manual**

    *list* *of str*, *optional*, *default = ' '*

    List of targets fieldnames for carrying out de calibration, the rest of the fields will not undergo direction-dependent calibration

  **de_sources_manual**

    *list* *of str*, *optional*, *default = ' '*

    List of sources per target to tag for DD calibration, in the same order as the de_target_manual list. Separate different sources per target by using ";".

  **sol_min_bl**

    *float*, *optional*, *default = 100*

    Min baseline length to solve for.

  **madmax_enable**

    *bool*, *optional*, *default = true*

    Enable madmax flagging in Cubical.

  **madmax_threshold**

    *list* *of int*, *optional*, *default = 0, 10*

    Threshold for MAD flagging per baseline (specified in sigmas). Residuals exceeding mad-thr\*MAD/1.428 will be flagged. MAD is computed per baseline. This can be specified as a list e.g. N1,N2,N3,... The first value is used to flag residuals before a solution starts (use 0 to disable), the next value is used when the residuals are first recomputed during the solution several iteratins later (see -chi-int), etc. A final pass may be done at the end of the solution. The last value in the list is reused if necessary. Using a list with gradually decreasing values may be sensible.

  **madmax_global_threshold**

    *list* *of int*, *optional*, *default = 0, 12*

    Threshold for global median MAD (MMAD) flagging. MMAD is computed as the median of the per-baseline MADs. Residuals exceeding S\*MMAD/1.428 will be flagged.

  **madmax_estimate**

    *str*, *optional*, *default = corr*

    MAD estimation mode. Use 'corr' for a separate estimate per each baseline and correlation. Otherwise, a single estimate per baseline is computed using 'all' correlations, or only the 'diag' or 'offdiag' correlations.

  **dd_data_column**

    *str*, *optional*, *default = CORRECTED_DATA*

    Column to calibrate

  **dd_out_data_column**

    *str*, *optional*, *default = SUBDD_DATA*

    Output data column

  **dd_weight_column**

    *str*, *optional*, *default = WEIGHT*

    Column to read weights from. Weights are applied by default. Specify an\nempty string to disable.

  **dd_sol_stall_quorum**

    *float*, *optional*, *default = 0.95*

    Minimum percentage of solutions which must have stalled before terminating\nthe solver.

  **dd_g_type**

    *str*, *optional*, *default = complex-2x2*

    Gain matrix type for g. Keep complex-2x2, because dd-cal fails otherwise.

  **dd_g_clip_high**

    *float*, *optional*, *default = 1.5*

    Amplitude clipping - flag solutions with any amplitudes above this value for g Jones

  **dd_g_clip_low**

    *float*, *optional*, *default = 0.5*

    Amplitude clipping - flag solutions with any amplitudes below this value for g Jones

  **dd_g_update_type**

    *str*, *optional*, *default = phase-diag*

    Determines update type. This does not change the Jones solver type, but restricts the update rule to pin the solutions within a certain subspace.

  **dd_g_max_prior_error**

    *float*, *optional*, *default = 0.35*

    Flag solution intervals where the prior error estimate is above this value for G-jones.

  **dd_g_max_post_error**

    *float*, *optional*, *default = 0.35*

    Flag solution intervals where the posterior variance estimate is above this value for G-jones.

  **dd_dd_max_prior_error**

    *float*, *optional*, *default = 0.35*

    Flag solution intervals where the prior error estimate is above this value for DE term.

  **dd_dd_max_post_error**

    *float*, *optional*, *default = 0.35*

    Flag solution intervals where the posterior variance estimate is above this value for DE term.

  **dd_g_timeslots_int**

    *int*, *optional*, *default = 10*

    Time solution interval in timeslot units for G-Jones.

  **dd_g_channel_int**

    *int*, *optional*, *default = 0*

    Frequency solution interval in channel units for G-Jones.

  **dd_dd_timeslots_int**

    *int*, *optional*, *default = 100*

    Time solution interval in timeslot units for DE-Jones.

  **dd_dd_channel_int**

    *int*, *optional*, *default = 100*

    Frequency solution interval in channel units for DE-Jones.

  **dist_nworker**

    *int*, *optional*, *default = 25*

    Number of processes



.. _ddcal_copy_data:

--------------------------------------------------
**copy_data**
--------------------------------------------------

  Copy DD-calibrated data to CORRECTED_DATA column

  **enable**

    *bool*, *optional*, *default = True*

    Enable copying of DD-calibrated data to CORRECTED_DATA column



.. _ddcal_image_wsclean:

--------------------------------------------------
**image_wsclean**
--------------------------------------------------

  Wsclean imaging paramaters for DD worker

  **enable**

    *bool*, *optional*, *default = True*

    Enable wsclean imaging of the DD-calibrated data.

  **img_ws_npix**

    *int*, *optional*, *default = 1800*

    Number of pixels in output image

  **img_ws_padding**

    *float*, *optional*, *default = 1.3*

    Padding in WSclean

  **img_ws_mgain**

    *float*, *optional*, *default = 0.90*

    Image CLEANing gain

  **img_ws_cell**

    *float*, *optional*, *default = 2.*

    Image pixel size (arcsec)

  **img_ws_weight**

    *{"briggs", "uniform", "natural"}*, *optional*, *default = briggs*

    Image weighting type. If Briggs, set the img robust parameter

  **img_ws_robust**

    *float*, *optional*, *default = 0.*

    Briggs robust value

  **img_ws_uvtaper**

    *str*, *optional*, *default = 0*

    Taper for imaging (arcsec)

  **img_ws_niter**

    *int*, *optional*, *default = 1000000*

    Number of cleaning iterations

  **img_ws_nmiter**

    *int*, *optional*, *default = 0*

    Number of major cycles

  **img_ws_cleanborder**

    *float*, *optional*, *default = 1.3*

    Clean border

  **img_ws_nchans**

    *int*, *optional*, *default = 3*

    Number of channesls in output image

  **img_ws_joinchannels**

    *bool*, *optional*, *default = True*

    Join channels to create MFS image

  **img_ws_fit_spectral_pol**

    *int*, *optional*, *default = 2*

    Number of spectral polynomial terms to fit to each clean component. This is equal to the order of the polynomial plus 1.

  **img_ws_pol**

    *str*, *optional*, *default = I*

    Stokes image to create

  **img_ws_auto_mask**

    *float*, *optional*, *default = 7*

    Auto masking threshold

  **img_ws_auto_threshold**

    *float*, *optional*, *default = 0.5*

    Auto clean threshold

  **img_ws_column**

    *str*, *optional*, *default = CORRECTED_DATA*

    Column to image

  **img_ws_fits_mask**

    *str*, *optional*, *default = catalog_mask.fits*

    filename of fits mask (in output/masking folder)

  **img_ws_multi_scale**

    *bool*, *optional*, *default = False*

    switch on multiscale cleaning

  **img_ws_multi_scale_scales**

    *list* *of int*, *optional*, *default = 10, 20, 30*

    scales of multiscale [0,10,20,etc, etc] in pixels

  **img_ws_local_rms**

    *bool*, *optional*, *default = False*

    switch on local rms measurement for cleaning



.. _ddcal_transfer_model_dd:

--------------------------------------------------
**transfer_model_dd**
--------------------------------------------------

  Repredict wsclean model to the highest channel resolution

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment (default False)

  **dd_model**

    *str*, *optional*, *default = auto*

    Name of the sky model file (currently the only supported format is that of WSclean component lists). When 'auto', the pipeline builds the file name from the input parameters of the selfcal loop. The file is assumed to be in the 'output' directory.

  **dd_spectra**

    *bool*, *optional*, *default = True*

    Model sources as non-flat spectra. The spectral coefficients and reference frequency must be present in the sky model.

  **dd_row_chunks**

    *int*, *optional*, *default = 0*

    Number of rows of input .MS that are processed in a single chunk.

  **dd_model_chunks**

    *int*, *optional*, *default = 0*

    Number of sky model components that are processed in a single chunk.

  **dd_exp-sign-convention**

    *str*, *optional*, *default = casa*

    Sign convention to use for the complex exponential. 'casa' specifies the e^(2.pi.I) convention while 'thompson' specifies the e^(-2.pi.I) convention in the white book and Fourier analysis literature. Defaults to 'casa'.

  **dd_within**

    *str*, *optional*, *default = ' '*

    Give JS9 region file. Only sources within those regions will be included.

  **dd_points_only**

    *bool*, *optional*, *default = False*

    Select only point-only sources. Default is False.

  **dd_num_sources**

    *int*, *optional*, *default = 0*

    Select only N brightest sources. Default is 0

  **dd_num_workers**

    *int*, *optional*, *default = 0*

    Explicitly set the number of worker threads. Default is 0, meaning it uses all threads.

  **dd_memory_fraction**

    *float*, *optional*, *default = 0.5*

    Fraction of system RAM that can be used. Used when setting automatically the chunk size.

