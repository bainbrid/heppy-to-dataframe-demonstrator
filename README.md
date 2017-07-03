# ra1-demonstrator
Demonstrate the use of AlphaTwirl in RA1 analyses

The final analaysis is built up in a series of steps, with each step being implemented as a `run.py`
file in the corresponding sub-directory of this package.  To see how each step builds on from the
previous step, it is worth looking at the diff between each steps.

The steps I want to take to get to a full demonstration are:
1. Local file - Make a dataframe with similar binning to RA1
2. Local file - Apply an event selection to Step 1
3. Local file - Add a scribbler to Step 2
4. Heppy file structure - Same as Step 3 but use a Heppy components directory as input
5. Heppy file structure - Add a "component name" scribbler to Step 4
6. Heppy file structure - Apply non-integer event weights on top of Step 5
7. Heppy file structure - Run Step 6 over all heppy components and use HTCondor to run jobs in parallel

# Dependence on the alphatwirl-interface repo
This package builds off the alphatwirl-interface repo which is still in development and therefore
fairly experimental.  Work here is likely to influence work there and vice versa, so things may
change often and significantly

# Usage
## Download and setup these scripts
It should be sufficient to checkout this package (and it's submodules), source the setup script and
start testing each step's run script.  These steps can be achieved by doing:
```
git clone --recursive git@github.com:benkrikler/ra1-demonstrator.git
cd ra1-demonstrator
source setup.sh
```
__Please note__ that I have only tested this on Bristol's Soolin so far, since that is where the RA1
trees are located.  In the final version of this package, it should work on any grid-connected
system.

## Running
It should be sufficient to change into the directory for the step you want to run, and execute the
run script.  For step2, for example, you can do:
```
$ cd step2_local_eventSelection/
$ ./run.py ../data/20170129_Summer16_newJECs--ZJetsToNuNu_HT100to200_madgraph--treeProducerSusyAlphaT--tree.root
```

Each run script can show you the options it accepts by doing:
```
./run.py --help
```
