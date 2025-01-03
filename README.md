# YOLO-ME
YOLO-ME model is developed for efficient object detection in aerial imagery using modified  YOLOv7 Tiny model.

**Setup prerequisites**

The following setup is for Windows 10 with an NVIDIA-supported GPU. Ensure all the prerequisites are installed correctly before proceeding.
1.	Python 3.7.7, 64 bit and numpy
2.	Git Version 2.26.2
3.	Cmake Version 3.17.2
4.	Visual Studio VS2019
5.	Updating latest NVIDIA GPU drives
6.	CUDA Version 10.2.89
7.	CuDnn Version 7.65 
8.	OpenCV Version 4.1.0 and OpenCV contrib
9.	Configure OpenCV using CMake
10.	Build OpenCV in Visual Studio

**Data preparation**

1.	Place the images and label files of the respective datasets in the ‘data’ folder.
2.	Create train.txt and test.txt files for the respective datasets. These files should list the image file paths relative to their directories.
3.	Create a .names file containing the class names of the dataset, one class per line. Place this file in the ‘visdrone’ folder.
4.	Create .data files for each dataset and place them in the ‘cfg’ folder. The .data file should include the following structure:

classes= 9
train  = visdrone/train.txt  
valid  = visdrone/test.txt  
names = visdrone/obj.names  
backup = backup/

5.	Place the YOLO-ME.cfg file in the ‘cfg’ folder.

**Training & testing**
1.	Run the following command to start training on the VisDrone dataset:
darknet.exe detector train cfg/obj_visdrone.data cfg/YOLO-ME_visdrone.cfg -map
2.	Use the following command to test the trained model:
darknet.exe detector test cfg/obj_visdrone.data cfg/ YOLO-ME_visdrone.weights -dont_show
3.	Run this command to evaluate the model's performance. mAP (Mean Average Precision):
darknet.exe detector map cfg/obj_visdrone.data cfg/ YOLO-ME_visdrone.weights -dont_show
