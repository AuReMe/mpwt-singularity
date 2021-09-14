mpwt Singularity recipe
=======================

Singularity recipe for `Pathway-Tools <https://bioinformatics.ai.sri.com/ptools/>`__ and `mpwt <https://github.com/AuReMe/mpwt>`__.
There is no guarantee that this recipe will work, it is a Work In Progress in early state.

There must be a Pathway Tools installer in the same folder than the ``Singularity`` file:

::

    directory
    ├── Singularity
    │
    ├── pathway-tools-25.0-linux-64-tier1-install

Once created, the size of the Singularity container is around 1.2 Gb.

To use Pathway-Tools, you need a file named .ncbirc in your home (the home location can be configured with Singularity by giving a path to the ``-H`` option) and containing the path to Blast:

::

    [ncbi]\nData=/usr/bin/data

To have an external ptools-local folder, we have implemented an ugly hack.
The idea is that it creates the ptools-local inside the home then it moves it inside the Singularity image.
After the creation of the container you have to use the command:

::

    cp -r /opt/ptools /home/your/external/folder/ptools

This will move the ptools-local folder (with permissions) from Singularity container to the local machine.

In this way, PGDBs can be stored in the home folder outside your container.

With some versions of Singularity (superior to 3.6) running ``singularity exec m2m.sif bash /cluster/myspace/m2m.sh`` will show the following error message:

::

    /bin/bash: /cluster/myspace/m2m.sh: No such file or directory

This error comes from modifications in Singularity linked to security issue. Especially the paths accessible to a container have been reduced. To fix this the ``-B`` option can be used to give access to Singularity to a specific path, for example:

::

    singularity exec -B /cluster/myspace/m2m:/cluster/myspace/m2m m2m.sif bash /cluster/myspace/m2m.sh
