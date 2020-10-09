Bootstrap: docker
From: ubuntu:18.04

%files
   pathway-tools-24.0-linux-64-tier1-install /opt

%environment
    export PATH="$PATH:/programs/pathway-tools:"
    export PYTHONIOENCODING=utf8

%post
     apt-get -y update && \
     DEBIAN_FRONTEND=noninteractive apt-get install -y \
     curl \
     csh \
     git \
     ncbi-blast+ \
     libxm4 \
     python3.6-dev \
     python3.6-distutils \
     iputils-ping \
     gnome-terminal;\
     apt-get clean; \
     apt-get purge; \
     mkdir programs;\
     mkdir -p /home/abelcour/Downloads/work_directory/programs/mpwt-singularity;\
     chmod u+x /opt/pathway-tools-24.0-linux-64-tier1-install;\
     ./opt/pathway-tools-24.0-linux-64-tier1-install --InstallDir /programs/pathway-tools --PTOOLS_LOCAL_PATH /home/abelcour/Downloads/work_directory/programs/mpwt-singularity --InstallDesktopShortcuts 0 --mode unattended;\
     mkdir -p /opt/ptools;\
     cp -r /home/abelcour/Downloads/work_directory/programs/mpwt-singularity/ptools-local /opt/ptools;\
     rm /opt/pathway-tools-24.0-linux-64-tier1-install;\
     curl https://bootstrap.pypa.io/get-pip.py | python3;\
     pip3 install https://github.com/AuReMe/mpwt/archive/master.zip