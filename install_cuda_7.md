# Install CUDA 7.0


## pre-install
```
$> sudo apt-get update
$> sudo apt-get install build-essential vim git
```

## Download
* Download [NVidia driver](http://www.nvidia.co.kr/Download/index.aspx) to ~/Download
* Download [CUDA run file installer bin file](https://developer.nvidia.com/cuda-downloads) to ~/Download

## Ready to install
```
$> cd ~/Downloads
$> sudo chmod +x NVIDIA-Linux-x86_64-352.41.run
$> ./cuda_7.0.28_linux.run -extract=~/Downloads/cuda_install
```

## Clear pre-install driver
```
// remove prev installed nvidia driver
$> sudo apt-get --purge remove nvidia-*

// disabled the Nouveau driver
$> sudo vim /etc/modprobe.d/blacklist.conf
$> (add new line at the end, and add this code) blacklist nouveau
$> sudo reboot
```

## Install NVidia driver
```

// After rebooting, Please directly switched to the terminal (using Ctrl + Alt + F1) and killed the X server to install the Nvidia driver
$> sudo service lightdm stop

// Install NVidia driver step: Accept >>> Continue installation >>> Install without signing >>> if warning just OK >>> OK >>> YES >>> OK >>>
$> sudo ~/Downloads/NVIDIA-Linux-x86_64-352.41.run
$> sudo modprobe nvidia
```

## Install CUDA 7.0.28
```
$> cd ~/Downloads/cuda_install
// Install step: accept >>> Enter >>> Enter >>> Enter
$> sudo ./cuda-linux64-rel-7.0.28-19326674.run
$> sudo ./cuda-samples-linux-7.0.28-19326674
```

## Test
```
//To test the installation
$> cd /usr/local/cuda/samples
$> cd 1_utilities/deviceQuery
$> sudo make
$> sudo ./deviceQuery
// If get Result PASS then install success
```

## Setting Environment
```
$> sudo service lightdm start
$> vim .bashrc
// add this two line to the end
export PATH=/usr/local/cuda-7.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-7.0/lib64:$LD_LIBRARY_PATH
$> source .bashrc
$> nvcc -V
// If get cuda version then set environment success
```
