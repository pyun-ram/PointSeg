## Training/Validation

```


## Train

```./train.sh -gpu 0 -image_set train -log_dir ./log/```

## eval

```./eval.sh -gpu 0 -image_set val -log_dir ./log/```

## requirement
``` 
easydict==1.6
joblib==0.10.3
numpy==1.12.0
Pillow==4.0.0
tensorflow-gpu>1.5
```
## Demo
This part is prepared for application on the velodyne with ros inference (test_demo.py) and visualization of results in rviz(demo.py)
### Additional requirement
```
ros-kinetic (ubuntu 16.04)
python-pcl (1.7)
```



## Run the demo
-   test_demo
    This file is used for real demo in ros and has written the projection in the file. To run this demo, you need to download the dataset from KITTI. And transfer it to the rosbag by yourself. If you have the velodyne, you can just pass this way and change the **lidar_topic** to the your device.
-  To transfer dataset into rosbag, you can check the https://github.com/tomas789/kitti2bag and follow the steps directly. (i am sorry i can not upload this for too big size)

```
cd src
python test_demo.py
rosbag play <data>.bag  ---- the bag which you transferrd from Kitti.
```
```
lidar_topic: /kitti/velo/pointcloud  # can be changed

publish:  1 points_raw
          2 points_raw 1-3  #car person cyclist
          
```
-  demo
    -  This file is used for the visualization, and do the segmentation on the file in **data/samples**, so if you want to see the result in rviz, just put the related dataset which you download from link, and run the demo.

```
cd src
python demo.py
```


**if you put more than one file in ''samples'' to see the results, please comment the ''while not rospy.is_shutdown():''**


