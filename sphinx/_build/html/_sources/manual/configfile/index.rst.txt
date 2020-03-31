.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _configfile:

==================
Configuration file
==================
 
.. toctree::
   :maxdepth: 1
 
Brief description of workers
----------------------------

Users settings are passed to Caracal through a .YML configuration file, which follows the
YAML rules (see https://yaml.readthedocs.io). The complete list of all parameters is
available at 

The following workers are available in Caracal. Typically, they are executed in the
same order in which they are given below. Only the first three workers (general, get_data
and  observation_config) should always be executed. All other workers are optional.

:ref:`general`
^^^^^^^^^^^^^^

This worker sets the name of various input/output directories
and the prefix used for the output data products (e.g., diagnostic plots, images, etc.).
 
