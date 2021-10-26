
## COMPILING C/C++ TO WASM AND RUNNING IT OUTSIDE WEB BROWSER
In this tutorial i will be compiling C programs to WASI and executing the compiled WebAssembly module using wasmtime runtime.

## Setting up enviroment
Upstream Clang and LLVM (from 9.0 onwards) can compile for WASI out of the box, and WebAssembly support is included in them by default. 

#### Download and install clang : 
    sudo apt install clang


## Compiling to WASI

The wasi-sdk provides a clang which is configured to target WASI and use the WASI sysroot by default if you put the extracted tree into /, so we can compile our program like so:

    clang demo.c -o demo.wasm
    
After running the above comand a .wasm file was generated in the source directory as show below
![image](https://user-images.githubusercontent.com/42975388/138921288-5de555a6-8e2f-48b5-bb9b-04eb4cb5294a.png)




## To run the wasm file

First Install wasmtime if not already installed in your machine. 
The wasmtime is a wasm runtime enviroment

The easiest way to install the wasmtime CLI tool is through our installation script. Linux and macOS users can execute the following:
    
    curl https://wasmtime.dev/install.sh -sSf | bash

This will download a precompiled version of wasmtime and place it in $HOME/.wasmtime, and update your shell configuration to place the right directory in PATH.
You can confirm your installation works by executing:

    wasmtime -V
    
    wasmtime 0.12.0


#### Executing in wasmtime runtime
I have tried running it with the following comands but failed. this where i am having problem.

    wasmtime demo.wasm
    
    echo hello world > test.txt

    wasmtime demo.wasm test.txt /tmp/somewhere.txt
    
the picture below shows the error message i got
![image](https://user-images.githubusercontent.com/42975388/138920397-48838185-874c-4d6a-bc0c-021617ef832b.png)

    
  
## MY Reference:
I followed this tutorial https://github.com/bytecodealliance/wasmtime/blob/main/docs/WASI-tutorial.md#executing-in-wasmtime-runtime
The c source i'm working with is also from there.


