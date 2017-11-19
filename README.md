# openfoam-windturbine
OpenFOAM case for a small wind turbine simulation.

The wind turbine is constructed with the following steps:
 1. Math: a few rough calculations using Python/Spyder
 2. QBlade: choice and assembly of airfoils
 3. FreeCAD: generation of rotor, nacelle and tower geometry with a Python script. Another script creates CFD computational domain(s) and exports it to STEP.
 4. OpenFOAM: STL file preparation is done in SALOME.

This is a simpleFoam/pimpleDyMFoam case consisting of 3 separate meshes, coupled with AMI: upstream, rotating and downstream. Obviously *rotating* part rotates and has all cells in *rotating* cellZone. Meshing is done exclusively with cfMesh. The RANS model used is k-Omega SST.

Bear in mind this is a heavily simplified case. The sole purpose of the simulation is to find out whether a cut-in speed of 1 m/s is enough for the designed turbine. The results probably aren't very accurate but they don't have to be anyway.

The workflow
./combineMeshes: combines meshes from upstream, rotating and downstream.
./decompose: copy 0.orig directory to 0 and decompose
./run: runs pimpleDyMFoam with MPI.
