# Image Convolution

This projects implements *Image Convolution* on 2D array.  
The project is composed of 3 functions:

 * `ImageConvolution()` - Implements image convolution using aribtrary sized input array and arbitrary size convolution kernel.
 * `ImageConvolutionSeparableKernel()`- Implements image convolution based on Separable Form of the Convolution Kernel.
 * `ImageConvolutionGaussianKernel()` - Implements image convolution by a Gaussian Isotropic Kernel by a simple wrapper on the `ImageConvolutionSeparableKernel()` function.



## Implementation Details

### Remarks
 * Currently the code implements Correlation and not Convolution. For convolution the user should reflect his kernel (Using `mReflectedConvKernel = rot90(mConvKernel, 2)` in MATLAB). Since most kernels in Image Processing are reflective in most cases it won't cause issues.
 * Currently the code uses *Replicate* / *Nearest Neighbor* Boundary Condition.
 * Due to use of SSE (SIMD Vectorization) the image number of columns must be a factor of 4.
 * Kernel dimensions must be odd in each dimension as its middle is the anchor of the convolution.

## How To Run
The project provides a full VS 2015 Solution file (Should be compatible with VS 2017).  
Since the code is written using basic C features it will compile on any system with C / C++ compiler.  
The project also provides ability to compile using GCC using a MATLAB script to automate the process.

### Visual Studio
 * Open the Solution File - `ImageConvolution.sln`.
 * Either generate an Executable or DLL using the defined projects.

### GCC
 * Run GCC command as shown in `GCC/CompileDllGcc.m` to Generate DLL.

### MATLAB
 * One could use the generated DLL in MATLAB as shown in `ImageConvolutionUnitTest001.m`, `ImageConvolutionUnitTest002.m` and `ImageConvolutionUnitTest003.m`.

## Release Notes
TBC

## Known Issues
 * The DLL generated by VS 2015 in Release Mode (Includes OpenMP support) crashes MATLAB. The DLL generated by GCC doesn't crash MATLAB.
 * Documentation is missing for `ImageConvolutionSeparableKernel()` and `ImageConvolutionSeparableKernel()`.
 * MSVC 2015 (Using `/02 /fp:fast /openmp`) yields 25% faster code than GCC (Using `-Ofast -fopenmp`). Verified in Executable.

## To Do List
 * Create an EXE which calculates the MFLOPS as a function of image size and Kernel Size.
 * Add support for Mirror and Periodic Boundary Conditions.
 * Make it faster.    
   If you can assist with that, please let me know.
 * 

## License
**DoWhatEverYouWant** License.
