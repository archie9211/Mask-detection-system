Mask Detection System using Yolov3 on custom made dataset : https://github.com/archie9211/Mask-Detection-Dataset

This project uses Yolov3 for the mask detection on live stream video from either webcam or cctv.


## Usage

clone the repo 
```
https://github.com/archie9211/majorProject/
cd majorProject
```

then download the yolo weights
```
wget https://my.gdrivemirror.workers.dev/yolov3_final.weights -O data/yolov3.weights
python convert.py
```

Running simple yolo on a video on webcam (--video 0) 

there are three modes of execution :

```
python run.py --video /path/to/video 
```
you can use another flag for saving the output to a video 

```
--video /path/to/video.mp4
```
run following command for full help of arguments and their uses :
```
python main.py --help
```
### for training:

this will need voc format dataset for training.

Example command line arguments for training

```
python train.py --batch_size 8 --dataset ~/Data/voc2012.tfrecord --val_dataset ~/Data/voc2012_val.tfrecord --epochs 100 --mode eager_tf --transfer fine_tune

python train.py --batch_size 8 --dataset ~/Data/voc2012.tfrecord --val_dataset ~/Data/voc2012_val.tfrecord --epochs 100 --mode fit --transfer none

python train.py --batch_size 8 --dataset ~/Data/voc2012.tfrecord --val_dataset ~/Data/voc2012_val.tfrecord --epochs 100 --mode fit --transfer no_output

python train.py --batch_size 8 --dataset ~/Data/voc2012.tfrecord --val_dataset ~/Data/voc2012_val.tfrecord --ep
```
for yolo format dataset training :
go to darknet folder
```
cd darknet
```
and make sure dataset is in imgs folder 

folder structure of darknet folder should be same as https://github.com/archie9211/Mask-Detection-Dataset

there is additional compiled binary of darknet

download pretrained weights for training 

```
wget https://my.gdrivemirror.workers.dev/darknet53.conv.74
```
for training
```
./darknet detector train "obj.data" "yolov3.cfg" "darknet53.conv.74"  -dont_show
```

you can also train over my weights
```
./darknet detector train "obj.data" "yolov3.cfg" "../data/yolov3.weights"  -dont_show
```

### Contributers :

    Nageen Chand (16MI523) 
