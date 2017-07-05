# CernVM
The examples in this folder are based on the [CernVM](https://cernvm.cern.ch/).
The CernVM provides access to the CernVM File System (CVMFS) which is a distributed,
on-demand file system that provides a plethora of software (e.g. ROOT, GEANT4, compilers)

Examples include one for Windows and one for Unix systems.

**NOTE:** By default these examples will use 2 cores and 2 GB of RAM.
If you want to adjust these numbers, please edit the Vagrantfile before starting up the VM.



## Example ROOT + GEANT4
```bash
vagrant up
vagrant ssh
source /cvmfs/sft.cern.ch/lcg/views/LCG_88/x86_64-slc6-gcc49-opt/setup.sh
```
