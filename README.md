﻿# sejabs.github.io
Configure number of processors available to MKL NumPy https://software.intel.com/en-us/forums/intel-distribution-for-python/topic/567669
  Welcome to the forum and thank you for the question!
  MKL uses the best number of threads by default, e.g. (on Windows):
  python -c "import ctypes; mkl_rt = ctypes.CDLL('mkl_rt.dll'); print mkl_rt.mkl_get_max_threads()"
  16
  If you want to change it, set MKL_NUM_THREADS environment variable to specify the number of threads to run in parallel, e.g.:
  set MKL_NUM_THREADS=1
  python -c "import ctypes; mkl_rt = ctypes.CDLL('mkl_rt.dll'); print mkl_rt.mkl_get_max_threads()"
  1
  How does one check the number of threads in linux?
  For linux, you need to change the name of the shared library:
  python -c "import ctypes; mkl_rt = ctypes.CDLL('libmkl_rt.so'); print(mkl_rt.mkl_get_max_threads())"
