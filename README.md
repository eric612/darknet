# Darknet retrain YOLOv2 in 4 classes (VOC0712) 

Train on VOC2007,2012 and test on VOC2007

Class|YOLOv2-416|YOLOv2-448|YOLOv2-320
:---:|:---:|:---:|:---:
bus|0.7804|0.7949|0.7536
car|0.7893|0.7955|0.7384
motorbike|0.7960|0.8042|0.7424
person|0.7475|0.7600|0.6909
mAP|0.7783|0.7886|0.7313

## Build

```
git clone https://github.com/eric612/darknet.git
cd $darknet_root
make 
```

## Data Prepare

cd $darknet_root/data/voc/

```
wget https://pjreddie.com/media/files/VOCtrainval_11-May-2012.tar
wget https://pjreddie.com/media/files/VOCtrainval_06-Nov-2007.tar
wget https://pjreddie.com/media/files/VOCtest_06-Nov-2007.tar
tar xf VOCtrainval_11-May-2012.tar
tar xf VOCtrainval_06-Nov-2007.tar
tar xf VOCtest_06-Nov-2007.tar 
python voc_label.py
cat 2007_train.txt 2007_val.txt 2012_*.txt > train.txt
```

## Vaild mAP

download [weights](https://drive.google.com/open?id=1kOO7gM_foAOTGy1fMpP2w7L_BXqxc-UZ) , save at $darknet root

cd $darknet_root/
```
sh valid.sh
sh calc_mAP.sh
```
## Train

* Unmark cfg/yolov2-voc.cfg training batch size

* cd $darknet_root/

```
wget https://pjreddie.com/media/files/darknet19_448.conv.23
./darknet detector train cfg/voc.data cfg/yolov2-voc.cfg darknet19_448.conv.23
```
## Python version 

If you meet the picke error , please unmark 
```
import _pickle as pickle
```
and mark
```
import cPickle
```
in file voc_eval_py3.py , reval_voc_py3.py

# Darknet #
Darknet is an open source neural network framework written in C and CUDA. It is fast, easy to install, and supports CPU and GPU computation.

For more information see the [Darknet project website](http://pjreddie.com/darknet).

For questions or issues please use the [Google Group](https://groups.google.com/forum/#!forum/darknet).
