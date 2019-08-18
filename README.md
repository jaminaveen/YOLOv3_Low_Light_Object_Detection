# YOLOv3_Low_Light_Object_Detection
This is a research project to understand the performance of YOLOv3 model in low light and find efficient ways to improve its performance in low light.
We have used the Exclusively Dark (ExDark). We have compared the mAP(mean Average Precision) of YOLOv3 obtained on COCO dataset to that of the mAP obtained on ExDark dataset and identified that the efficiency of the algorithm is very less in low light when compared to normal image dataset. This research sums up the contrast-based image enhancement techniques applied to preprocess our dataset and compared the results with our benchmark obtained on original ExDark dataset. Also we have compared the training YOLOv3 from scratch and transfer learning techniques.
 
 
Steps :
 [1]  Clone this file
$ git clone https://github.com/HarshithaGS/Object_Detection_in_Low_Light.git
[2] Dependencies to run the code
$ pip install -r ./docs/requirements.txt
[3] Exporting loaded COCO weights as TF checkpoint(yolov3_coco.ckpt)
$ cd YOLO
$ wget https://github.com/YunYang1994/tensorflowyolov3/releases/download/v1.0/yolov3_coco.tar.gz
tar -xvf yolov3_coco.tar.gz
 
[4] Data preprocessing to get all images from ExDark and ExDark_Anno into a folder called train and create dataset .txt

[5] Testing on ExDark data set to obtain the Benchmark mAP

Edit the file  $ cd core/config.py  to make necessary configurations.

__C.YOLO.CLASSES                = "./data/classes/coco.names"
__C.TEST.ANNOT_PATH             = "./data/dataset/dataset.txt"

Testing and Evaluation
$ python evaluate.py
$ cd mAP
$ python main.py -na





