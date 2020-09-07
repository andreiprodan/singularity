Bootstrap: docker
From: ubuntu:20.04

%runscript
    exec echo "This is an Ubuntu 20.04 LTS Container with Miniconda!!"

%files
   
%environment
   CONDA_INSTALL_PATH="/usr/local/miniconda3"
   CONDA_BIN_PATH="/usr/local/miniconda3/bin"
   export PATH="$CONDA_BIN_PATH:$PATH"

%labels
   OWNER andreiprodan

%post
   echo "The post section is where you can install, and configure your container."  
   apt-get update && apt-get -y install wget     # Installing commonly used apps
   wget https://repo.anaconda.com/miniconda/Miniconda3-py38_4.8.3-Linux-x86_64.sh    # download and install Anaconda (miniconda, conda v.4.8.3)
   chmod +x Miniconda3-py38_4.8.3-Linux-x86_64.sh
   CONDA_INSTALL_PATH="/usr/local/miniconda3"
   ./Miniconda3-py38_4.8.3-Linux-x86_64.sh -b -p $CONDA_INSTALL_PATH
   rm Miniconda3-py38_4.8.3-Linux-x86_64.sh
   export PATH="/usr/local/miniconda3/bin:$PATH"      # cant create environments without this
   #conda install -c conda-forge mamba      # Install mamba (better package dependency resolution than classical conda)
   #mamba create -y -c conda-forge -c bioconda -n snakemake snakemake=5.23.0       # Install snakemake v5.23.0 with mamba