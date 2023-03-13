# Champsim Resources

## Installation

```
sudo docker pull cs232ta/champsim-docker:latest

# For first time usage:
sudo docker run --name cs232 -v <absolute-path-of-folder-in-your-machine>:/shared_folder -it cs232ta/champsim-docker


# For further usage:
sudo docker start cs232
sudo docker exec -it cs232 /bin/bash
```

## Working inside the docker container
* A few sample programs are provided in the `/champsim/programs` folder
* compile them as follows:
```g++ -o <binary-file> <program-file>``` 
* Setting up the pin tool: Navigate to `/champsim/Champsim/tracer` folder and run `./make_tracer.sh`. A folder named `obj-intel64` would've been created.
* Navigate to the `/champsim/pin_v3.17` folder, and run:
```./pin -t /champsim/Champsim/tracer/obj-intel64/champsim-tracer.so -o /champsim/traces/<trace-name>.trace -- /champsim/programs/<binary-file>```
There are few more options to the above command, you can look at them in the docs.
* Navigate to the `/champsim/traces` folder, and run the following command:
```xz -z9v <trace-name>.trace```
* Navigate to the `/champsim/Champsim` folder, and run:
```./build_champsim.sh [branch_pred] [l1i_pref] [l1d_pref] [l2c_pref] [llc_pref] [llc_repl] [num_core]```
Here, the options are for the L1I, L1D, L2, LLC prefetchers and the LLC replacement policy and the number of cores. To use the default set them as `no`. Else, use the specific name of the prefetcher/policy you need. Here is an example of a basic command: 
```./build_champsim.sh bimodal no no no no lru 1```
* Now, we need to run the `run_champsim.sh` file:
```./run_champsim.sh [BINARY] [N_WARM] [N_SIM] [TRACE] [OPTION]```
  * The binary is inside the bin folder, just provide the name of the binary(don't give the absolute path) 
  * N_WARM and N_SIM are in units of 10M 
  * The trace __should be__ inside the traces folder, just provide the name of the trace(don't give the absolute path) 
  * Look at `run_champsim.sh` to tweak and make your own changes
* There will be a `results-<num>M` folder created, which contains the results of the trace. Make sure to save these results to your machine, as it gets overwritten everytime.

