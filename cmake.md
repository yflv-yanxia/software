# template
    cmake_minimum_required (VERSION 2.8)

    project (Demo)

    SET(CMAKE_BUILD_TYPE Release ON)
    add_compile_options(-std=c++11)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}  -std=c++0x")

    include_directories ( 
        ./include
        /usr/local/include
        /usr/local/cuda/include
        /usr/include 
        /opt/OpenBLAS/include
        )

    add_executable(Demo 
        ../src/main.cpp
        )

    target_link_libraries(Demo 
        /usr/lib64/libopencv_core.so
        /usr/lib64/libopencv_highgui.so
        /usr/lib64/libopencv_imgproc.so
        /usr/lib64/libglog.so
        /usr/lib64/libboost_system.so
        /usr/lib64/libpthread.so
        )
