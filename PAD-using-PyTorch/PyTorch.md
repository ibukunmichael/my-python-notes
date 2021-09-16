# **Python Application Development Using PyTorch** #
PyTorch is an open source machine learning library for Python, based on Torch, used for applications such as natural language processing. It is primarily developed by Facebook's artificial-intelligence research group, and Uber's "Pyro" software for probabilistic programming is built on it.
 
 <!--images-->
![Getting Started](./pytorch1.png)

PyTorch is a python package that provides two high-level features:
-	Tensor computation (like numpy) with strong GPU acceleration
-	Deep Neural Networks built on a tape-based autodiff system
You can reuse your favorite python packages such as numpy, scipy and Cython to extend PyTorch when needed.

Usually one uses PyTorch either as:
-	A replacement for numpy to use the power of GPUs.
-	A deep learning research platform that provides maximum flexibility and speed
Elaborating further:
A GPU-ready Tensor library
If you use numpy, then you have used Tensors (a.k.a ndarray).

  <!--images-->
![Getting Started](./pytorch2.png)

PyTorch provides Tensors that can live either on the CPU or the GPU, and accelerate compute by a huge amount.
It provides a wide variety of tensor routines to accelerate and fit your scientific computation needs such as slicing, indexing, math operations, linear algebra, reductions. And they are fast!
### **Python first** ###
PyTorch is not a Python binding into a monolothic C++ framework. It is built to be deeply integrated into Python. You can use it naturally like you would use numpy / scipy / scikit-learn etc. You can write your new neural network layers in Python itself, using your favorite libraries and use packages such as Cython and Numba. 
### **Imperative experiences** ###
PyTorch is designed to be intuitive, linear in thought and easy to use. When you execute a line of code, it gets executed. There isn’t an asynchronous view of the world. When you drop into a debugger, or receive error messages and stack traces, understanding them is straight-forward. The stack-trace points to exactly where your code was defined. 
### **Fast and Lean** ###
PyTorch has minimal framework overhead. It has integrated acceleration libraries such as Intel MKL and NVIDIA (CuDNN, NCCL) to maximize speed. At the core, its CPU and GPU Tensor and Neural Network backends (TH, THC, THNN, THCUNN) are written as independent libraries with a C99 API. They are mature and have been tested for years.
Hence, PyTorch is quite fast – whether you run small or large neural networks.
The memory usage in PyTorch is extremely efficient compared to Torch or some of the alternatives. It has custom memory allocators for the GPU to make sure that your deep learning models are maximally memory efficient. This enables you to train bigger deep learning models than before.
### **Extensions without pain** ###
Writing new neural network modules, or interfacing with PyTorch’s Tensor API was designed to be straight-forward and with minimal abstractions.
You can write new neural network layers in Python using the torch API or your favorite numpy based libraries such as SciPy
If you want to write your layers in C/C++, an extension API based on cffi that is efficient and with minimal boilerplate is provided.
There is no wrapper code that needs to be written. You can see examples at https://github.com/pytorch/examples/ and tutorials at https://github.com/pytorch/tutorials

