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
 
Users settings are passed to Caracal through a .YML configuration file. This must follow
the YAML syntax rules (see https://yaml.readthedocs.io). The complete list of al parameters
that can be set with the configuration file is available at :ref:`workers`.

Most parameters are optional and do not need to be included in the configuration file.
Their default values are set to work in as many cases as possible. A few parameters are
compulsory. The pages at :ref:`workers` indicate whether a parameter is optional, its data
type, allowed values (if necessary) and default value.

Caracal comes with a set of sample configuration files. These are available at
caracal/sample_configurations and include:

* minimalConfig.yml, which includes as few parameters as possible and performs a basic
  data reduction;
* meerkat-continuum-defaults.yml, which is optimised for the reduction of data taken with
  the MeerKAT telescope for the purpose of total-intensity continuum imaging.

Users could take these sample configuration files as a starting point for their work.