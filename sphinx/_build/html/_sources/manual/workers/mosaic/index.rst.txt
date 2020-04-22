.. caracal documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _mosaic:
 
==========================================
mosaic
==========================================
 
.. toctree::
   :maxdepth: 1
 
Mosaic the images and cubes made with the self_cal and image_line workers. If not available on disc, the primary beam is built by this worker assuming a Gaussian shape with FWHM = 1.02 lambda/D.



.. _mosaic_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute mosaic segment.



.. _mosaic_target_images:

--------------------------------------------------
**target_images**
--------------------------------------------------

  *seq*, *optional*, *default = directory/first_image.fits, directory/second_image.fits*

  List of images to be mosaicked, with suffix of image.fits being expected.



.. _mosaic_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*, *default = corr*

  For autoselection of images, this needs to match the label setting used for the self_cal worker (when mosaicking continuum images) or the image_line worker (when mosaicking cubes).



.. _mosaic_line_name:

--------------------------------------------------
**line_name**
--------------------------------------------------

  *str*, *optional*, *default = HI*

  Spectral mode only -- If autoselection is used to find the final cubes, this needs to match the line_name parameter used for the image_line_worker.



.. _mosaic_mosaic_type:

--------------------------------------------------
**mosaic_type**
--------------------------------------------------

  *{"continuum", "spectral"}*

  Type of mosaic to be made, either continuum or spectral.



.. _mosaic_use_MFS_images:

--------------------------------------------------
**use_MFS_images**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  Indicate that the images to be mosaicked were created using MFS.



.. _mosaic_name:

--------------------------------------------------
**name**
--------------------------------------------------

  *str*, *optional*, *default = ' '*

  The prefix to be used for output files. Default is the pipeline prefix(pipeline.prefix).



.. _mosaic_domontage:

--------------------------------------------------
**domontage**
--------------------------------------------------

  Re-grid the input images, and associated beams.

  **enable**

    *bool*, *optional*, *default = True*

    Execute this domontage section.



.. _mosaic_cutoff:

--------------------------------------------------
**cutoff**
--------------------------------------------------

  *float*, *optional*, *default = 0.1*

  The cutoff in the primary beam. It should be a number between 0 and 1.



.. _mosaic_dish_diameter:

--------------------------------------------------
**dish_diameter**
--------------------------------------------------

  *float*, *optional*, *default = 13.5*

  If no continuum pb.fits are already in place, user needs to specify the dish diameter(in units of m) so that rudimentary primary beams can be created.



.. _mosaic_ref_frequency:

--------------------------------------------------
**ref_frequency**
--------------------------------------------------

  *float*, *optional*, *default = 1383685546.875*

  If no continuum pb.fits are already in place, user needs to specify the reference frequency(in units of Hz) so that rudimentary primary beams can be created.

