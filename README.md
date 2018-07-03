# Darknet retrain YOLOv2 in 4 classes (VOC0712) 

Network|Resolution|mAP|bus|car|motorbike|person
:---:|:---:|:---:|:---:|:---:|:---:|:---:
YOLOv2|448x448|0.7699|0.7837|0.7925|0.7600|0.7437

## Data Prepare

cd $darknet/data/voc/

```
wget https://pjreddie.com/media/files/VOCtrainval_11-May-2012.tar
wget https://pjreddie.com/media/files/VOCtrainval_06-Nov-2007.tar
wget https://pjreddie.com/media/files/VOCtest_06-Nov-2007.tar
tar xf VOCtrainval_11-May-2012.tar
tar xf VOCtrainval_06-Nov-2007.tar
tar xf VOCtest_06-Nov-2007.tar 
```

## Vaild mAP

cd $darknet/

```
sh valid.sh
sh calc_mAP.sh
```
## Training

cd $darknet/
wget https://pjreddie.com/media/files/darknet19_448.conv.23
```
./darknet detector train cfg/voc.data cfg/yolov2-voc.cfg darknet19_448.conv.23
```

# Darknet #
Darknet is an open source neural network framework written in C and CUDA. It is fast, easy to install, and supports CPU and GPU computation.

For more information see the [Darknet project website](http://pjreddie.com/darknet).

For questions or issues please use the [Google Group](https://groups.google.com/forum/#!forum/darknet).
