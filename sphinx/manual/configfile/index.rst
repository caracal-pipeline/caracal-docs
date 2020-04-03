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
 
Users settings are passed to Caracal through a configuration file. This consists of a
sequence of blocks, one per run of a Caracal worker. Within each block the worker's
parameters are arranged in a nested structure following the YAML syntax rules
(see https://yaml.readthedocs.io). As an example, a block of the config file may look like::

  some_worker:
    enable: true
    parameter1: value1
    parameter2:
      subpar1: value2_1
      subpar2: value2_2
    parameter3: value3

The complete list of all workers' parameters that users can set through the configuration file is available at :ref:`workers`,
where the parameters' nesting is also explained.

Most parameters are optional and do not need to be included in the configuration file.
Their default values are set to work in as many cases as possible. A few parameters are
compulsory. The pages at :ref:`workers` indicate whether a parameter is optional, its data
type, allowed values (if necessary) and default value.

Caracal comes with a set of sample configuration files. These are available at
caracal/sample_configurations/ and include:

* minimalConfig.yml, which includes as few parameters as possible and performs a basic
  data reduction including both continuum and spectral line imaging;
* meerkat-continuum-defaults.yml, which is optimised for the reduction of data taken with
  the MeerKAT telescope for the purpose of total-intensity continuum imaging.

Users could take these sample configuration files as a starting point for their work.