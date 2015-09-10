# Install OpenBLAS and Boost

## Install OpenBLAS
```
$> sudo apt-get install gfortran
$> cd ~/Downloads
$> git clone git://github.com/xianyi/OpenBLAS
$> cd OpenBLAS
$> make -j $(nproc)
$> sudo make PREFIX=/usr/local install
```

## Install Boost
```
$> sudo apt-get install libboost-all-dev
```
