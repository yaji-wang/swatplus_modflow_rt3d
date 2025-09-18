## Linux command lines for compiling source codes into .exe

## steps
1. Load compiler (feel free to replace with your own)
2. Configure the project with CMake
3. Build with CMake

```bash
module load intel/2022.2.1
cmake -B build -D CMAKE_Fortran_COMPILER=ifort
cmake --build build
