## caffe dependency
    Anaconda python
    CMake
    FFmpeg
    Opencv
    boost
    gflags
    glog
    protobuf
    snappy
    leveldb
    lmdb
    hdf5
    OpenBLAS
    mkl
    libunwind
    apache-maven
    freetype
    harfbuzz
    cudnn
    pydot
    nccl
# tools
[A web-based tool for visualizing neural network architectures](http://ethereon.github.io/netscope/quickstart.html), [git](https://github.com/ethereon/netscope)<br>

# disable logging
## method1
    If you want to turn off log from code level, you can use this.

    Just add below line in your c++ code at src/caffe/net.cpp in Init method and build caffe:

    fLI::FLAGS_minloglevel=3;
    Partial view of the function where this line should be added:

    template <typename Dtype>
    void Net<Dtype>::Init(const NetParameter& in_param) {

      fLI::FLAGS_minloglevel=3;


      // Set phase from the state.
      phase_ = in_param.state().phase();
      // Filter layers based on their include/exclude rules and
      
## method2
    google::InitGoogleLogging("PAL");
    //google::SetCommandLineOption("GLOG_minloglevel", "2");
    FLAGS_stderrthreshold = google::ERROR;
    
    google::ShutdownGoogleLogging();
    
# accelerate
    batch
    remove batchnorm in deployment
    multi-thread
    sort by gpu
    reduce timestep
    
