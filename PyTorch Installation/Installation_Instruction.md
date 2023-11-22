Install the necessary packages using the requirements.txt file

```
pip install -r requirements.txt
```


1) Move to the directory
```
cd YOLOv3-Object-Detection-with-OpenCV
```

2) To infer on an image that is stored on your local machine
```
python3 yolo.py --image-path='/path/to/image/'
```
Note: When inferring for the first time, use the command 
```
python3 yolo.py --image-path='/path/to/image/' --download-model=True
```
this will download the weights. Move the weights in the ./yolov3-coco folder
