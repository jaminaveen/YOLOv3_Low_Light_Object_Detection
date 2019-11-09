# YOLOv3_Low_Light_Object_Detection
This is a research project to understand the performance of YOLOv3 model in low light and find efficient ways to improve its performance in low light.
We have used the Exclusively Dark (ExDark) dataset. We have compared the mAP(mean Average Precision) of YOLOv3 obtained on COCO dataset to that of the mAP obtained on ExDark dataset and identified that the efficiency of the algorithm is very less in low light when compared to normal image dataset. This research sums up the contrast-based image enhancement techniques applied to preprocess our dataset and compared the results with our benchmark obtained on original ExDark dataset. Also we have compared the training YOLOv3 from scratch and transfer learning techniques.
 
 
Steps :

[1]  Clone this file

         $ git clone https://github.com/jaminaveen/YOLOv3_Low_Light_Object_Detection/
         
[2] Download the ExDark data from the link : https://github.com/cs-chan/Exclusively-Dark-Image-Dataset

[3] Dependencies to run the code

         $ pip install -r ./docs/requirements.txt

[4] Exporting loaded COCO weights as TF checkpoint(yolov3_coco.ckpt)
                 
         $ cd YOLO
         $ wget wget https://pjreddie.com/media/files/yolov3.weights
 
[5] Data preprocessing to get all images from ExDark and ExDark_Anno into a folder called test_benchmark folder and creating annotations file called test_benchmark.txt, test_he.txt, test_dhe.txt,test_ying.txt are present in /data/dataset/ folder. We have also uploaded notebooks in the same folder that will guide through the generation of annotations file.

    Annotation files should be in following format
     xxx/xxx.jpg 18.19,6.32,424.13,421.83,20 323.86,2.65,640.0,421.94,20
     xxx/xxx.jpg 48,240,195,371,11 8,12,352,498,14
     # image_path x_min, y_min, x_max, y_max, class_id  x_min, y_min ,..., class_id 

         
[6] Testing on ExDark data set to obtain the Benchmark mAP

---> Edit the file  $ cd core/config.py  to make necessary configurations.

    __C.YOLO.CLASSES                = "./data/classes/coco.names"
    __C.TEST.ANNOT_PATH             = "./data/dataset/test_benchmark.txt"

---> Testing and Evaluation
         
         $ python test.py
         $ python ../mAP/main.py

[7] Applying the histogram equalization enhancement technique on the ExDark data.

---> Run the $ he.py code to perform the image contrast enhancement. The enhanced images are saved in the path /data/dataset/he_train
---> Run the dataprep.py to obtain the annotations path as dataset_he.txt in the path /data/dataset/dataset_he.txt
---> Edit the file  $ cd core/config.py  to make necessary configurations.

     __C.TEST.ANNOT_PATH             = "./data/dataset/test_he.txt"
  
---> Now run the test.py to test the YOLOv3 on the he enhanced images
---> Evaluate the performance by computing the mAP score. To do this :

      $ python ..mAP/main.py

[8] Applying the dynamic histogram equalization enhancement technique on the ExDark data.

---> Run the $ dhe.py code to perform the image contrast enhancement. The enhanced images are saved in the path /data/dataset/dhe_train
---> Run the dataprep.py to obtain the annotations path as dataset_he.txt in the path /data/dataset/dataset_dhe.txt
---> Edit the file  $ cd core/config.py  to make necessary configurations.

     __C.TEST.ANNOT_PATH             = "./data/dataset/test_dhe.txt"
  
---> Now run the test.py to test the YOLOv3 on the dhe enhanced images
---> Evaluate the performance by computing the mAP score. To do this :

               $ cd mAP
               $ python main.py -na

[9] Applying the exposure fusion framework enhancement technique on the ExDark data.

---> Run the $ Ying.py code to perform the image contrast enhancement. The enhanced images are saved in the path /data/dataset/ying_train
---> Run the dataprep.py to obtain the annotations path as dataset_ying.txt in the path /data/dataset/dataset_ying.txt
---> Edit the file  $ cd core/config.py  to make necessary configurations.

     __C.TEST.ANNOT_PATH             = "./data/dataset/test_ying.txt"
  
---> Now run the test.py to test the YOLOv3 on the he enhanced images
---> Evaluate the performance by computing the mAP score. To do this :
 
                  python ..mAP/main.py

[10] Code for transfer learning and fine tuning on final layers is present in train_yolov3_darkdata.ipynb

[11] Insights we found on low light images using  ExDark dataset were documented in our paper. Please refer our ([Research paper](https://github.com/jaminaveen/YOLOv3_Low_Light_Object_Detection/blob/master/Research_paper.pdf))


#### Reference:

  1. https://github.com/YunYang1994/TensorFlow2.0-Examples/tree/master/4-Object_Detection/YOLOV3 













