# Procedural Execution Reference

### Procedural Execution

This unikernels demonstrates a more advanced use of MirageManager. Besieds the variable
values, additional inforamtion about the state of execution is stored and transmitted 
to the repository. 
After a resumption the execution state will be reconstructed from the received 
state document and execution will resume from the previous location in 
exectuion space. In addition the value of all variables will also be restored.
The position in the execution space is fully specified by the value of the last
computational step executed and the value of the variables at that point.
Instead of racing a functionality and a control promise, Xenstore is only read
in between computational steps. 
If a control message is received, the unikernel will act upon it accordingly.
The adjacency matrix is defined as a function, so that boolean constraints on 
the transitions are evaluated dynamically at transition time.
Each computational step is defined as a function that returns a unit promise and
takes a store objects. A mapping links them to their string identifiers.
If the program is done, the terminate function is called.
The execution of the steps is performed within the recursive run function.
### Build

The build is automatic and can be invoked by running the `build_kernel.sh` script.
This will build one Xen image for DHCP unikernels and on for static IP unikernels.
Both must be uploaded to git, for MirageManager to be able to use them.