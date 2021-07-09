- Original repository for gpu installer is from here [coreosgpuinstaller](https://github.com/shelmangroup/coreos-gpu-installer/)
- The following modifications have already been made in this repo. So no new modifications required
-     a. Change ubuntu to 18.04 in Dockerfile and add the following environment variables.

        ENV NVIDIA_INSTALL_DIR_HOST /opt/nvidia
        ENV NVIDIA_INSTALL_DIR_CONTAINER /usr/local/nvidia
        ENV ROOT_MOUNT_DIR /root
        ENV ROOT_OS_RELEASE /etc/os-release

    b. Change the entrypoint.sh to use the kernel version available in coreos. In order to get the kernel version, run this command on the host (edge) --> uname -r | cut -d- -f1
    c. Hardcode this directly in entrypoint.sh 
        Example: KERNEL_SRC_ARCHIVE="linux-4.19.50.tar.xz" (Note: 4.19.50 is the kernel version that I had)

    d. Hardcode the nvidia driver version as 440.100 as nvidia seems to have this version as the max supported version for kernel version 4.19.50


- k8s-nvidia-deviceplugin.yaml plugin has been taken from [k8scoreosdriver](https://github.com/gardener/gpu-installer)
- Follow the instructions from ndac_edge_gpu_install_steps.txt