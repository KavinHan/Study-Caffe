# Install Caffe

## Download
```
$> cd ~/Downloads
$> git clone https://github.com/BVLC/caffe.git
```

## Install
```
$> mv caffe/ ~/
$>  cd ~/caffe/
$> cp Makefile.config.example Makefile.config
$> sed -i 's/# USE_CUDNN := 1/USE_CUDNN := 1/' Makefile.config
$> sed -i 's/BLAS := atlas/BLAS := open/' Makefile.config
$>  for req in $(cat python/requirements.txt); do pip install $req; done
$> sudo pip install -r python/requirements.txt
$> make all -j $(nproc)
```
**If make error: cv::imread(cv::String const&, int)' .build_release/lib/libcaffe.so:.....**
**[Solution link](https://github.com/BVLC/caffe/issues/2348)**
> I meet the same problem and make a solution. add "opencv_imgcodecs" in Makefile.(LIBRARIES += glog gflags protobuf leveldb snappy \ lmdb boost_system hdf5_hl hdf5 m \opencv_core opencv_highgui opencv_imgproc opencv_imgcodecs) If you input "make all",the problem is the same again.But if you delete all the file in build(rm -rf ./build/*) before "make all",you will success

```
$> make pycaffe -j $(nproc)
$> echo "export CAFFE_ROOT=$(pwd)" >> ~/.bashrc
$> echo 'export PYTHONPATH=$CAFFE_ROOT/python:$PYTHONPATH' >> ~/.bashrc
$> source ~/.bashrc
```

## Test
```
$> ipython
$> import caffe
// If no error then install success
```
