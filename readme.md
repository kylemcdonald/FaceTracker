# FaceTracker

FaceTracker is a library for deformable face tracking written in C++ using OpenCV 2, authored by [Jason Saragih](http://jsaragih.org/) and maintained by [Kyle McDonald](http://kylemcdonald.net/).

It is available free for non-commercial use, and may be redistributed under these conditions. Please see `license.md` for complete details. For commercial use, [request a quote](http://facetracker.net/quote/).

Wrappers are available for:

* [openFrameworks](http://www.openframeworks.cc/): [ofxFaceTracker](https://github.com/kylemcdonald/ofxFaceTracker)
* [Cinder](http://libcinder.org/): [ciFaceTracker](https://github.com/Hebali/ciFaceTracker)
* Python: [pyfacetracker](https://bitbucket.org/amitibo/pyfacetracker)

## Installation

These instructions are for compiling the code on OS X and Ubuntu, but it should be possible to compile on other platforms.

First, install OpenCV-2.x. This code has been tested with OpenCV-2.0 and OpenCV-2.4. On OSX you can use `[brew](http://brew.sh/) install opencv` and on Ubuntu use `sudo apt-get install libcv-dev libopencv-dev`. Alternatively, you can download the repository from `git clone git://code.opencv.org/opencv.git` and compile it manually.

Then, clone this repository with `git clone git://github.com/kylemcdonald/FaceTracker.git`. This repository contains a few subdirectories within the root directory:
   - src (contains all source code)
   - model (contains a pre-trained tracking model)
   - bin (will contain the executable after building)

Next, make sure that your copy of OpenCV is located in `/usr/local` (this should be the case if you used `brew` or `apt-get`). If it isn't located there, modify the `OPENCV_PATH` in the `Makefile`. Optionally, you can also add `-fopenmp` to the `CFLAGS` and `-lgomp` to `LIBRARIES` to compile with [OpenMP](http://openmp.org/) support.

From the root `FaceTracker` directory, build the library and example by running `make`.

To test the demo, `cd bin` and `./face_tracker`. Because many webcams are 1280x720, try running `./face_tracker -s .25` to rescale the image before processing for a smoother framerate.

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
