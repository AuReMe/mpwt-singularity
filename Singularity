Bootstrap: docker
From: ubuntu:20.04

%files
   pathway-tools-25.0-linux-64-tier1-install /opt

%environment
    export PATH="$PATH:/programs/pathway-tools:"
    export PYTHONIOENCODING=utf8

%post
     echo "deb http://security.ubuntu.com/ubuntu bionic-security main" >> /etc/apt/sources.list ;\
     apt-get -y update && \
     DEBIAN_FRONTEND=noninteractive apt-get install -y \
     ssh-client \
     curl \
     csh \
     git \
     ncbi-blast+ \
     python3-pip \
     libxm4 \
     libssl1.0-dev \
     iputils-ping \
     gnome-terminal;\
     apt-get clean; \
     apt-get purge; \
     mkdir programs;\
     mkdir -p /home/your/external/folder/ptools;\
     chmod u+x /opt/pathway-tools-25.0-linux-64-tier1-install;\
     ./opt/pathway-tools-25.0-linux-64-tier1-install --InstallDir /programs/pathway-tools --PTOOLS_LOCAL_PATH /home/your/external/folder/ptools --InstallDesktopShortcuts 0 --mode unattended;\
     mkdir -p /opt/ptools;\
     cp -r /home/your/external/folder/ptools/ptools-local /opt/ptools;\
     rm /opt/pathway-tools-25.0-linux-64-tier1-install;\
     pip install --upgrade setuptools ;\
     pip3 install mpwt