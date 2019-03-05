mpwt Singularity recipe
=======================

Singularity recipe for Pathway-Tools and mpwt.
There is no guarantee that this recipe will work, it is a Work In Progress in early state.

To use Pathway-Tools, you need a file named .ncbirc in your home and containing the path to Blast:

[ncbi]\nData=/usr/bin/data

To have an external ptools folder (mandatory when using big data), we have implemented an ugly hack.
The idea is that it creates the ptools-local inside the home then it moves it inside the Singularity image.

After the creation of the container you have to use the command:

cp -r /opt/ptools /home/your/external/folder/ptools

This will move the ptools-local folder (with permissions) from Singularity container to the local machine.

In this way, PGDBs can be stored in the home folder outside your container.
