





# YOLACT-Building-AR
This study presents two major systems designed for automotive driver assistance. The first is a Forward Safety Warning System, which utilizes the [YOLACT](https://github.com/dbolya/yolact) real-time segmentation algorithm to identify the center point of objects ahead. It then calculates distances to these objects using 3D point cloud data from two [ZED 2i stereo cameras](https://www.stereolabs.com/zed-2i/) to provide warnings. The second system is an Augmented Reality Advertisement System for buildings. It employs the YOLACT segmentation algorithm to recognize buildings, estimates their approximate polygon sides and outer dimensions, and displays promotional videos for various campus departments using augmented reality techniques.

## YOLACT
[YOLACT](https://github.com/dbolya/yolact) is a real-time instance segmentation model that was proposed in 2019. It is a one-stage model, which means that it predicts the bounding boxes and masks of objects in a single pass. YOLACT achieves state-of-the-art results on the [COCO dataset](https://cocodataset.org/#home), while running at over 30 frames per second on a single GPU.

## Feature
* Introducing MobilenetV2 as the Backbone speeds up training and significantly reduces inference time.
* Utilizing two ZED 2i stereo cameras to achieve a wide-angle system and enable distance measurement.
* Detecting various departmental buildings within an effective distance through feature recognition,like the image below:

![建築物廣告系統介紹](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/f7158bb2-73d3-4bf1-96e9-7f45471cb996)
  
### Results
* Building AR System

| Dept. of Electrical Engineering | Dept. of Mechanical Engineering | Dept. of Industrial Design | Dept. of Applied Foreign Languages | Dept. of Creative Design |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| ![電機系] (https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/c9493f2b-c0fb-4027-afee-773227798acd) |![機械系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/89dd5aaa-7544-48ff-9ac6-3edd6ca4b4a2) | ![工設系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/5d4e1abb-a1f5-4d72-a39a-ddb4ae39ab69) | ![應外系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/9b7f23c0-062e-48b9-8fa3-22843b6d7fac) | ![產設系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/28fd801c-e58a-4da7-a4ce-678ed58a3a09) | 

* Lane Detection System (Use ZED 2i Stereo Camera)

![類別_腳踏車_左](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/1df63394-548c-4eff-a80b-02ad6977b988)

