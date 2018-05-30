# template
    cmake_minimum_required (VERSION 2.8)

    # variable
    set(OBJ_NAME Demo)
    
    project ($(OBJ_NAME))
    

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

    aux_source_directory(./src DIR_SRCS)
    add_executable(${OBJ_NAME} ${DIR_SRCS})
    #add_executable($(OBJ_NAME) 
    #    ../src/main.cpp
    #    )

    target_link_libraries($(OBJ_NAME) 
        /usr/lib64/libopencv_core.so
        /usr/lib64/libopencv_highgui.so
        /usr/lib64/libopencv_imgproc.so
        /usr/lib64/libglog.so
        /usr/lib64/libboost_system.so
        /usr/lib64/libpthread.so
        )
    #install (TARGETS ${OBJ_NAME} DESTINATION bin)
