## platform
    pycharm
    eclipse
    
## install
    if slowly from offical web, fetch it from mirror webs, https://npm.taobao.org/mirrors/python/2.7.15/
    pip: https://pypi.org/project/pip/#description
    选择 pip-10.0.1.tar.gz 文件, 解压，python setup.py install 
    
## import c
    extern "C" int square(int x);
    extern "C" int square(int x)
    {
      return x*x;
    }

    import ctypes
    print(ctypes.windll.library.square(4)) # windows
    print(ctypes.CDLL('./library.so').square(4)) # linux or when mingw used on windows
