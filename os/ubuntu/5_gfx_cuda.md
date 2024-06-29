

## Graphics Card / CUDA


    # sudo apt remove --autoremove nvidia-*
    # sudo apt-get --purge remove libnvidia-*
    sudo apt install -y nvidia-driver-535

- Check drivers installation:
    - Prints Graphics Card Info, CUDA is version supported, not installed

    nvidia-smi

- Install CUDA

    # Install CUDA
    # 1. https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=22.04&target_type=deb_local
    # DONT use network DEB!
    cd ~/Downloads
    wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin
    sudo mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600
    wget https://developer.download.nvidia.com/compute/cuda/12.3.1/local_installers/cuda-repo-ubuntu2204-12-3-local_12.3.1-545.23.08-1_amd64.deb
    sudo dpkg -i cuda-repo-ubuntu2204-12-3-local_12.3.1-545.23.08-1_amd64.deb
    sudo cp /var/cuda-repo-ubuntu2204-12-3-local/cuda-*-keyring.gpg /usr/share/keyrings/
    sudo apt-get update
    sudo apt-get -y install cuda-toolkit-12-3 

- Check CUDA version:

   nvcc --version

# Stable Diffusion setup:

- Install this beforehand:

    sudo apt-get install libgoogle-perftools4 libtcmalloc-minimal4 -y

- Then follow:
    
    https://www.youtube.com/watch?v=n0u2Kfu2Cbs
