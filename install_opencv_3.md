# Install OpenCV 3.0

## Download
* Download [OpenCV3.0 for Linux/Mac](http://opencv.org/downloads.html) to ~/Downloads

## Install requirement
```
$> sudo apt-get -y install libopencv-dev cmake libgtk2.0-dev pkg-config python-dev python-numpy libdc1394-22 libdc1394-22-dev libjpeg-dev libpng12-dev libtiff4-dev libjasper-dev libavcodec-dev libavformat-dev libswscale-dev libxine-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libv4l-dev libtbb-dev libqt4-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev x264 v4l-utils unzip
```

##Unzip
```
$> cd ~/Downloads
$> unzip opencv-3.0.0.zip
```

## Compile
```
$> mv opencv-3.0.0.zip ~/
$> cd ~/opencv-3.0.0
$> mkdir build
$> cd build
$> cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_TBB=ON -D BUILD_NEW_PYTHON_SUPPORT=ON -D WITH_V4L=ON -D INSTALL_C_EXAMPLES=ON -D INSTALL_PYTHON_EXAMPLES=ON -D BUILD_EXAMPLES=ON -D WITH_QT=ON -D WITH_OPENGL=ON -D ENABLE_FAST_MATH=1 -D CUDA_FAST_MATH=1 -D WITH_CUBLAS=1 ..
// If Error: ...libGL.so...
$> sudo rm /usr/lib/x86_64-linux-gnu/libGL.so
$> sudo ln -s /usr/lib/libGL.so.1 /usr/lib/x86_64-linux-gnu/libGL.so
$> make -j $(nproc)
```

## Install
```
$> sudo make install
$> sudo /bin/bash -c 'echo "/usr/local/lib" > /etc/ld.so.conf.d/opencv.conf'
$> sudo ldconfig
```

## Test
```
$> cd ~/opencv-3.0.0/samples/
$> sudo cmake .
$> sudo make -j $(nproc)
$> cd cpp/
$> ./cpp-example-facedetect ../data/lena.jpg
// If show circle on lena face, then install success
```
