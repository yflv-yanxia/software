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
    extern "C" int add(int a, int b);
    extern "C" int addf(float a, float b);
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
    extern "C" int test( void* p, int len);
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
    print(a,b,c)
