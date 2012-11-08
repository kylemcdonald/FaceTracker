# FaceTracker

FaceTracker is a library for deformable face tracking written in C++ using OpenCV 2, authored by [Jason Saragih](http://jsaragih.org/) and maintained by [Kyle McDonald](http://kylemcdonald.net/).

It is available free for non-commercial use, and may be redistributed under these conditions. Please see `license.md` for complete details.

Wrappers are available for:

* [openFrameworks](http://www.openframeworks.cc/): [ofxFaceTracker](https://github.com/kylemcdonald/ofxFaceTracker)
* [Cinder](http://libcinder.org/): [ciFaceTracker](https://github.com/Hebali/ciFaceTracker)
* Python: [pyfacetracker](https://bitbucket.org/amitibo/pyfacetracker)

## Installation

These instructions are for compiling the code on OS X only. Compilation on other Unix-type architectures should be similar.

1. Download the latest version of OpenCV-2.0 with `git clone git://code.opencv.org/opencv.git` (more instructions [here](http://code.opencv.org/projects/opencv/wiki/Working_with_OpenCV_git_repository))
2. Follow the OpenCv [installation instructions](http://opencv.willowgarage.com/wiki/Mac_OS_X_OpenCV_Port) and compile and install OpenCV to some arbitrary local directory (usually `/usr/local/`).
3. Clone the FaceTracker code with `git clone git://github.com/kylemcdonald/FaceTracker.git`. This will number of subdirectories within the root directory:
   - src (contains all source code)
   - model (contains a pre-trained tracking model)
   - bin (will contain the executable after building)
4. In the `Makefile` located in the root directory of the FaceTracker code, change the `OPECV_PATH` variable to the directory where OpenCV was installed (by defualt `/usr/local`). Optionally, you can also add `-fopenmp` to the `CFLAGS` and `-lgomp` to `LIBRARIES` to compile with [OpenMP](http://openmp.org/) support.
5. Build the system with `make`.
6. The executable `face_tracker` can be found in the `bin` subdirectory.

## `face_tracker` Usage

````
Usage: face_tracker [options]
Options:
-m <string> : Tracker model (default: ../model/face2.tracker)
-c <string> : Connectivity (default: ../model/face.con)
-t <string> : Triangulation (default: ../model/face.tri)
-s <double> : Image scaling (default: 1)
-d <int>    : Frames/detections (default: -1)
--check     : Check for failure 
--help      : Print help
-?          : Print help
````
