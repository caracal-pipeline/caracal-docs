# Download & Install

## Usage and publication policy

When using CARACal please be aware of and adhere to the [CARACal publication policy](https://docs.google.com/document/d/12LjHM_e1G4kWRfCLcz0GgM8rlXOny23vVdcriiA8ayU).

## Software requirements and supported platforms
Most dependencies are taken care of by using [pip](https://pypi.org/project/pip/) and [PiPy](https://pypi.org) to control Python dependencies and [Stimela](https://github.com/ratt-ru/Stimela/tree/master/stimela) as a platform-independent scripting framework. This leaves a small number of known dependencies (currently only one) that need to be installed prior to using CARACal:
- [Python](https://www.python.org/) 3.6 or higher
- [Singularity](https://github.com/sylabs/singularity) > 2.6.0-dist is required only if [Singularity](https://github.com/sylabs/singularity) is chosen as containerization technology to run [Stimela](https://github.com/ratt-ru/Stimela/tree/master/stimela) with (no known [Docker](https://www.docker.com/) dependencies).

CARACal fully supports [Docker](https://www.docker.com/) and [Singularity](https://github.com/sylabs/singularity). It is also possible to use it in combination with [Podman](https://podman.io/).

## Installing and running CARACal

Shell-style is used to indicate names and paths of directories and files which can be chosen by the user: ``${name}``.

### Installing and running manually
We recommend and describe an installation using a virtual environment created with [Virtualenv](https://virtualenv.pypa.io/en/latest/). This is not a requirement, but strongly recommended.
The user chooses:
- the name (including path) ${caracal-venv} of the virtualenv
- the location ``${singularity_pull_folder}`` of a [Singularity](https://github.com/sylabs/singularity) pull-folder, where [Singularity](https://github.com/sylabs/singularity) images are stored (not required when using only [Docker](https://www.docker.com/) or [Podman](https://podman.io/), the latter currently not being fully supported).
#### Manual installation
The latest CARACal release can be obtained by typing:
```
$ python3 -m venv ${caracal-venv}  
$ source ${caracal-venv}/bin/activate
$ pip install -U pip setuptools wheel
$ pip install -U caracal
```
Using [Docker](https://www.docker.com/):
```
$ stimela build
```
Using [Singularity](https://github.com/sylabs/singularity) (choose a [Singularity](https://github.com/sylabs/singularity) pull-folder ``${singularity_pull_folder}``):  

```  
$ stimela pull --singularity --pull-folder ${singularity_pull_folder}
```

Using [Podman](https://podman.io/) (currently not fully supported):
```
$ stimela pull -p
```
Please see [Installing a Python 3 virtualenv](#Installing-a-Python-3-virtualenv) for more information on virtualenv.

##### Current development branch
*Warning: the current development branch obviously contains the most recent developments but it might contain bugs.*
It is also possible not to install the release version but instead the current development version of CARACal. 

*Warning: the current development branch obviously contains the most recent developments but it might contain bugs. We take no responsibility for development versions of CARACal.*

Do do so, replace above pip installation of CARACal 
```
pip install -U caracal
```
with:
```
$ pip install -U git+https://github.com/ska-sa/caracal.git#egg=caracal
```
#### Running CARACal manually
The user needs to know the name ``${caracal-venv}`` of the virtualenv used during the installation and the name ``${singularity_pull_folder}`` of the [Singularity](https://github.com/sylabs/singularity) pull folder used when installing CARACal. For the most basic usage, the user generally chooses:
- the name ${my_caracal_run_dir} (and hence the location) of a folder in which the data reduction takes place
- a template configuration file ``${template_config}`` to use for the data reduction, as can be downloaded (and re-named to your choice) from the [sample_configurations](https://github.com/ska-sa/caracal/tree/master/caracal/sample_configurations) folder in the CARACal repository. To start, we recommend to use [``minimal_config.yml``](https://github.com/ska-sa/caracal/blob/master/caracal/sample_configurations/minimalConfig.yml).
- a name for the final configuration file ``${my_config_file}`` to use.

An example run then looks like:
```
$ mkdir ${my_caracal_run_dir}
$ cd ${my_caracal_run_dir}
```
Copy ``${template_config}`` into ``${my_caracal_run_dir}``, then re-name (this is strictly not necessary):
```
$ mv ${template_config} ${my_config_file}
```
Create ``msdir`` inside ``${my_caracal_run_dir}`` 
```
$ mkdir ${my_caracal_run_dir}/msdir
```
and move/copy your raw measurement set files into that directory. Edit your ``${my_config_file}`` to link to those files. If the names of your measurement sets are ``a.ms b.ms c.ms``, then edit the line
```
dataid=[] -> dataid=['a','b','c']
```
in ${my_config_file}. Do analogously for different names of your measurement sets.

Finally, run CARACal, after activating your virtualenv:
```
$ source ${caracal-venv}/bin/activate
```
Using [Docker](https://www.docker.com/):
```
$ caracal -c ${my_config_file}
```
Using [Singularity](https://github.com/sylabs/singularity) (using the [Singularity](https://github.com/sylabs/singularity) pull-folder ``${singularity_pull_folder}`` created during the installation):  

```  
$ caracal -c ${my_config_file} --container-tech singularity -sid ${singularity_pull_folder}
```
Using podman (currently not fully supported):
```
$ caracal -c ${my_config_file} --container-tech podman
```
#### Upgrading a manual CARACal installation
The following steps should lead to an upgraded CARACal:
Activate your virtualenv:
```
$ source ${caracal-venv}/bin/activate
```
Then run the following commands, like outlined in [Manual installation](#Manual-installation):
```
$ pip install -U caracal
```
Using [Docker](https://www.docker.com/):
```
$ stimela build
```
Using [Singularity](https://github.com/sylabs/singularity) (choose a [Singularity](https://github.com/sylabs/singularity) pull-folder ``${singularity_pull_folder}``):  

```  
$ stimela pull --singularity --pull-folder ${singularity_pull_folder}
```

Using [Podman](https://podman.io/) (currently not fully supported):
```
$ stimela pull -p
```
Please see [Stimela cache file](#stimela-cache-file) for troubleshooting for a more forceful upgrade.

##### Current development branch
*Warning: the current development branch obviously contains the most recent developments but it might contain bugs.*
It is also possible not to install the release version but instead the current development version of CARACal. 

*Warning: the current development branch obviously contains the most recent developments but it might contain bugs. We take no responsibility for development versions of CARACal.*

Do do so, replace above pip installation of CARACal 
```
pip install -U --force-reinstall caracal
```
with:
```
$ pip install -U --force-reinstall git+https://github.com/ska-sa/caracal.git#egg=caracal
```
### Installation using caratekit.sh

To newly install CARACal using caratekit, download [caratekit.sh](https://github.com/ska-sa/caracal/raw/master/caracal/utils/caratekit.sh) and make it executable (alternatively clone caracal and find ``caratekit.sh`` ):
```
$ chmod u+x caratekit.sh 
```
Then select a parent directory ``$parent`` (e.g. ``/home/pete``) to the installation and a name $installation_name (e.g. ``caracal``) for the installation. Then do:
```
caratekit.sh -ws $parent -ct  $installation_name -kh -di -op -ur
```
for a docker installation and:
```
caratekit.sh -ws $parent -ct  $installation_name -kh -si -op -ur -sr
```
for a singularity installation.

Each time you want to run caracal using the docker installation do:

``$ source $parent/$installation_name/caracal_venv/bin/activate`` (bash)
or
``> source $parent/$installation_name/caracal_venv/bin/activate.csh`` (csh or tcsh)
then create a data reduction directory $datared and put the configuration file $config.yml into that directory. Also create a directory msdir in $datared and put your raw measurement set data sets therein. Then

``$ cd $datared``

``$ caracal -c $config.yml`` (Docker)

``$ caracal -c $config.yml --container-tech singularity -sid $parent/$installation_name/stimela_singularity`` (Singularity)

For details on caratekit.sh type ``$ caratekit.sh -h`` or ``$ caratekit.sh -v``.
## Using CARACal
After activating the virtualenv
```
$ source ${caracal-venv}/bin/activate
```
CARACal has several switches. In its entirety, they can be accessed by invoking help.
### Getting help
```
$ caracal --help
```
### Dumping a copy of the minimal default configuration file to the current directory
```
$ caracal -gd ${configuration_file}
```
where ${configuration_file} is the target name of the configuration file.
