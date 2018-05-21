# platform
    pycharm
    eclipse
    
# install
    if slowly from offical web, fetch it from mirror webs, https://npm.taobao.org/mirrors/python/2.7.15/
    pip: https://pypi.org/project/pip/#description
    选择 pip-10.0.1.tar.gz 文件, 解压，python setup.py install 
    
# import c
    https://www.cnblogs.com/night-ride-depart/p/4907613.html
## function
    extern "C" int add(int a, int b)
    {
      return a + b;
    }
     extern "C" int addf(float a, float b)
    {
      return a + b;
    }

    import ctypes
    so_pointer = ctypes.CDLL('./library.so')
    #so_pointer = ctypes.CDLL('./library.dll')
    #so_pointer = ctypes.windll.library

    so_pointer.addf.argtypes = (ctypes.c_float, ctypes.c_float)
    so_pointer.addf.restype = ctypes.c_float
    print(so_pointer.add(2, 3))
    print(so_pointer.addf(2.5, 3.5))
    print(so_pointer.addf(ctypes.c_float(2.5), ctypes.c_float(3.5)))
## char*
    extern "C" int test( void* p, int len)
    {
         return len;
    }  

    buff = 'weidazhongguo'
    test.argtypes = (ctypes.c_char_p, ctypes.c_int)
    test.restype = ctypes.c_int
    length = test(buff, len(buff))
    
## struct
    class Point(ctypes.Structure):
        _fields_ = [("x", c_float), ("y", c_float)]
    p = Point(2,5)  
    p.x = 3 
    print (p.x, p.y) 
    
## pointer
    extern "C" int addff(float a, float* b)
    {
      *b = a;
      return a + (*b);
    }

    so_pointer.addff.argtypes = (ctypes.c_float, ctypes.POINTER(ctypes.c_float))
    so_pointer.addff.restype = ctypes.c_float  
    a = 2
    b = ctypes.c_float(3)
    c = so_pointer.addff(a, ctypes.pointer(b))
    print(a,b.value,c)
## array
    #include <stdlib.h>
    #include <stdint.h>
    __declspec(dllexport) void read(int16_t* input, size_t size)
    {
      int i;
      for(i=0;i<size;i++)
        input[i] = i;
    }

    from ctypes import *
    x = CDLL('x')
    x.read.argtypes = (POINTER(c_int16),)
    x.read.restype = None
    p = (c_int16*5)()
    x.read(p,len(p))
    print(list(p))

    -------------
    #include <stdlib.h>
    #include <stdint.h>
    __declspec(dllexport) void read(int16_t** input, size_t size)
    {
      int i;
      int16_t* p = (int16_t*) malloc (size*sizeof(int16_t));
      for(i=0;i<size;i++)
        p[i] = i;
      *input = p;
    }
    __declspec(dllexport) void release(int16_t* input)
    {
        free(input);
    }

    from ctypes import *
    x = CDLL('x')
    x.read.argtypes = [POINTER(POINTER(c_int16))]
    x.read.restype = None
    x.release.argtypes = [POINTER(c_int16)]
    x.release.restype = None
    p = POINTER(c_int16)()
    x.read(p,5)
    for i in range(5):
        print(p[i])
    x.release(p)

    #if array defined in python
    pyarr = [1, 2, 3, 4]
    arr = (ctypes.c_int * len(pyarr))(*pyarr)
    result_c = (ctypes.c_char * step_num)()
