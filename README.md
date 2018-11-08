# Darknet retrain YOLOv2 in 4 classes (VOC0712) 

Train on VOC2007,2012 and test on VOC2007

Class|YOLOv2-416|YOLOv2-448|YOLOv2-320
:---:|:---:|:---:|:---:
bus|0.836|0.839|0.816
car|0.822|0.839|0.780
motorbike|0.837|0.8042|0.781
person|0.775|0.780|0.724
mAP|0.8135|0.8238|0.7752

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

download [weights](https://drive.google.com/open?id=15aMa8R8FlnQv6Tl2lvQYWSZBo6xK4jWV) , save at $darknet root

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
