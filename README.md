# ML_computer_vision_realtime_traffic_detection_dlib_opencv_python_sandeep_kanao
ML_computer_vision_realtime_traffic_detection_dlib_opencv_python_sandeep_kanao

python traffic_object_counter.py --prototxt mobilenet_ssd/MobileNetSSD_deploy.prototxt 	--model mobilenet_ssd/MobileNetSSD_deploy.caffemodel --input videos/traffic-1.mp4 	--output output/traffic-1-count.avi

In this part we will build a “traffic object (car, trucks, bikes etc.) counter” with OpenCV and Python. Using OpenCV, we’ll count the number of traffic objects who are heading “in” or “out”  in real-time.

Required Python libraries 
In order to build the application, we’ll need a number of different Python libraries, including:

NumPy
OpenCV
dlib
imutils


Understanding  object tracking --Sandeep Kanao

An object tracker, on the other hand, will accept the input (x, y)-coordinates of where an object is in an image and will:

Assign a unique ID to that particular object
Track the object as it moves around a video stream, predicting the new object location in the next frame based on various attributes of the frame (gradient, optical flow, etc.)
Examples of object tracking algorithms include MedianFlow, MOSSE, GOTURN, kernalized correlation filters, and discriminative correlation filters, to name a few.

Combining both object detection and object tracking - Sandeep Kanao
Highly accurate object trackers will combine the concept of object detection and object tracking into a single algorithm, typically divided into two phases:

Phase 1 — Detecting: During the detection phase we are running our computationally more expensive object tracker to (1) detect if new objects have entered our view, and (2) see if we can find objects that were “lost” during the tracking phase. For each detected object we create or update an object tracker with the new bounding box coordinates. Since our object detector is more computationally expensive we only run this phase once every N frames.
Phase 2 — Tracking: When we are not in the “detecting” phase we are in the “tracking” phase. For each of our detected objects, we create an object tracker to track the object as it moves around the frame. Our object tracker should be faster and more efficient than the object detector. We’ll continue tracking until we’ve reached the N-th frame and then re-run our object detector. The entire process then repeats.

To implement our traffic object counter we’ll be using both OpenCV and dlib. We’ll use OpenCV for standard computer vision/image processing functions, along with the deep learning object detector for people counting.

We’ll then use dlib for its implementation of correlation filters. We could use OpenCV here as well; however, the dlib object tracking implementation was a bit easier to work with for this project.

Reference : https://www.pyimagesearch.com/2018/08/13/opencv-people-counter/
YouTube Output : https://youtu.be/7aecg1YYlxI
