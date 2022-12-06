# Oligomer

**Part-A:**

The MD input files, parameter files, and topology files can be found in MD.zip file. 

One can run the MD using the following steps.

**Energy Minimization**

gmx_mpi grompp -f em-steep.mdp -c NAC8_ionized.gro -p topol.top -n index.ndx -o em.tpr
gmx_mpi mdrun -s em.tpr -deffnm em


**NPT heating**

gmx_mpi grompp -f npt-heating.mdp -c NAC8_ionized.gro -p topol.top -n index.ndx -o npt-heating.tpr
gmx_mpi mdrun -s npt-heating.tpr -deffnm npt-heating


**NPT Equilibration**

gmx_mpi grompp -f npt-equilibrium.mdp -c npt-heating.gro -p topol.top -n index.ndx -t npt-heating.cpt -o npt-equilibrium.tpr
gmx_mpi mdrun -s npt-equilibrium.tpr -deffnm npt-equilibrium


**NPT Prduction Run**

gmx_mpi grompp -f production_run_npt.mdp -c npt-equilibrium.gro -p topol.top -n index.ndx -t npt-equilibrium.cpt -o npt-production.tpr
gmx_mpi mdrun -s npt-production.tpr -deffnm npt-production


After performing Part-A, one needs to follow the Part-B for subsequent analysis

**Part-B:**

The codes and corresponding input files are in the Oligomer_program.zip file in code. First unzip the xdrf directory,
then compile the program by

f95 ./xdrf/xtciof.o ./xdrf/libxdrf.a -lm Program.F90

following by ./a.out <file.inp 

If one has trajectory file then he/she can easily complie the program.
