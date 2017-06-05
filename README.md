# OpenCVTraining
## Introduction

This repository holds documents used to create haarcascade of some objects, as well as the cascades themselves.

Training utilizes only one image of the object to be identified, and is likely to be highly specific.

Steps:
* Ensure neg folder is in working folder
* Ensure create_pos_neg.py is in working folder
* Create data folder - mkdir data
* Create info folder - mkdir info
* Generate bg.txt - python3 create_pos_neg.py
* Generate pool of positive samples by overlaying positive over negative images (replace image name) - opencv_createsamples 
-img watch_resized.jpg -bg bg.txt -info info/info.lst -pngoutput info -maxxangle 0.5 -maxyangl
e 0.5 -maxzangle 0.5 -num 1950
* Create vector file - opencv_createsamples -info info/info.lst -num 1950 -w 20 -h 20 -vec positives.vec
* Run cascade trainer (add nohup to allow trainer to keep running even when terminal is closed - opencv_traincascade -data data -vec positives.vec -bg bg.txt -numPos 1800 -numNeg 900 -numStages 10 -w 20 -h 20

