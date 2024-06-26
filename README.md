# rf2na-packages
Script to solve the package dependency issues for [RoseTTAFold2NA](https://github.com/uw-ipd/RoseTTAFold2NA).

As of 2024-04-17, the `main` branch has many issues with unmet package dependencies, some examples below

`NVTX functions not installed`

`Cannot load Graphbolt C++ library`

Missing packages such as `torchdata`, `pandas` and `pydantic` 

These issues have been documented at least in Issues #104, #99, #94, #93, #37, #36 and #33.

After quite a bit of trial and error, the following steps/script works for installing packages and is able to run through the example dataset.  
  
---
**Developed and tested on**  
**OS**: Ubuntu 22.04.4 LTS  
**Nvidia Driver**: 550.54.15  
**CUDA**: 12.4  
**conda**: 24.3.0  

---
This shell script takes care of dependencies in [RF2na-linux.yml](https://github.com/uw-ipd/RoseTTAFold2NA/blob/main/RF2na-linux.yml) and [SE3Transformer/requirements.txt](https://github.com/uw-ipd/RoseTTAFold2NA/blob/main/SE3Transformer/requirements.txt)

After cloning the RoseTTAFold2NA repository, place the below shell script in the `RoseTTAFold2NA` directory.  
Execute as `$ source create_env.sh`

All needed packages are installed, skip additional steps for SE3Transformer.

Download the above `create_env.sh` script.

Also documented are the conda YAML (not tested) and conda table of packages.

Hope this is helpful!   

---   

Created a Databases file to download them in parallel, since some of them can be a slow download and take several days.
The below command spawns 4 wget processes, and each process handles one file download, logging is quieted.

`cat databases.txt | xargs -n 1 -P 4 wget -q`


 


