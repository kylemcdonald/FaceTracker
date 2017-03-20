# FaceTracker

FaceTracker is a library for deformable face tracking written in C++ using OpenCV 2, authored by [Jason Saragih](http://jsaragih.org/) and maintained by [Kyle McDonald](http://kylemcdonald.net/).

It is available free for non-commercial use, and may be redistributed under these conditions. Please see `license.md` for complete details. For commercial use, [request a quote](http://facetracker.net/quote/).

## FAQ

1. **"I successfully compiled the code, so why is my app is crashing?"** Make sure that your model files are in the right location. If you see the error `Assertion failed: s.is_open()` when running your app, that means you forgot to put the model files in the right directory.
2. **"Is there an example of using FaceTracker on a mobile device?"** There is no official example. But there is an example of using ofxFaceTracker on iOS [here](https://github.com/kylemcdonald/ofxFaceTracker-iOS) and a native Android example [here](https://github.com/ajdroid/facetrackerapp).
3. **"Why is the tracking is slow, and why is there high CPU usage?"** The face detection step (finding the general location of the face) can be slow. If this is causing an issue, you might want to put the tracking in a separate thread. If the detection is very slow you might try using a face detector that is native to your platform, and initializing FaceTracker with that rectangle.

Wrappers are available for:

* Android: [facetrackerapp](https://github.com/ajdroid/facetrackerapp)
* [openFrameworks](http://www.openframeworks.cc/): [ofxFaceTracker](https://github.com/kylemcdonald/ofxFaceTracker)
* [Cinder](http://libcinder.org/): [ciFaceTracker](https://github.com/Hebali/ciFaceTracker)
* Python: [pyfacetracker](https://bitbucket.org/amitibo/pyfacetracker)

## Installation

These instructions are for compiling the code on OS X and Ubuntu, but it should be possible to compile on other platforms.

First, install OpenCV3 (if you're using OpenCV2, use the [opencv2](https://github.com/kylemcdonald/FaceTracker/tree/opencv2) branch of this repo). On OSX you can use [homebrew](http://brew.sh/):

```
$ brew tap homebrew/science
$ brew install homebrew
```

And on Ubuntu use:

```
$ sudo apt-get install libcv-dev libopencv-dev
```

Alternatively, you can download [OpenCV from the GitHub](https://github.com/opencv/opencv) and compile it manually.

After installing OpenCV, clone this repository with `git clone git://github.com/kylemcdonald/FaceTracker.git`. This repository contains a few subdirectories within the root directory:
   - src (contains all source code)
   - model (contains a pre-trained tracking model)
   - bin (will contain the executable after building)

Next, make sure that your copy of OpenCV is located in `/usr/local` (this should be the case if you used `apt-get`). If it isn't located there, modify the `OPENCV_PATH` in the `Makefile`. If you installed with Homebrew, it should be set to `/usr/local/opt/opencv3`.

Optionally, you can also add `-fopenmp` to the `CFLAGS` and `-lgomp` to the `LIBRARIES` variable to compile with [OpenMP](http://openmp.org/) support.

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