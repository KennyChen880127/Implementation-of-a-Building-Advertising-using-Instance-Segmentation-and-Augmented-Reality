





# YOLACT-Building-AR
This study presents two major systems designed for automotive driver assistance. The first is a Forward Safety Warning System, which utilizes the [YOLACT](https://github.com/dbolya/yolact) real-time segmentation algorithm to identify the center point of objects ahead. It then calculates distances to these objects using 3D point cloud data from two [ZED 2i stereo cameras](https://www.stereolabs.com/zed-2i/) to provide warnings. The second system is an Augmented Reality Advertisement System for buildings. It employs the YOLACT segmentation algorithm to recognize buildings, estimates their approximate polygon sides and outer dimensions, and displays promotional videos for various campus departments using augmented reality techniques.

## YOLACT
[YOLACT](https://github.com/dbolya/yolact) is a real-time instance segmentation model that was proposed in 2019. It is a one-stage model, which means that it predicts the bounding boxes and masks of objects in a single pass. YOLACT achieves state-of-the-art results on the [COCO dataset](https://cocodataset.org/#home), while running at over 30 frames per second on a single GPU.

## Feature
* Introducing MobilenetV2 as the Backbone speeds up training and significantly reduces inference time.
* Utilizing two ZED 2i stereo cameras to achieve a wide-angle system and enable distance measurement.
* Detecting various departmental buildings within an effective distance through feature recognition,like the image below:

![介紹辨識建築物](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/62714fc9-9365-4bab-83b7-b4c0db3e2973)
  
### Results
* Building AR System

| Dept. of Electrical Engineering | Dept. of Mechanical Engineering | Dept. of Industrial Design | Dept. of Applied Foreign Languages | Dept. of Creative Design |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| ![電機系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/92ea3b31-f933-4402-b175-60ddbde38c69) | ![機械系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/123d0137-d303-4712-ac30-0d1876b864d1) | ![工設系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/242e4cf9-ddc0-46af-b7a2-4f64815f558e) | ![應外系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/ba452533-e75f-4909-b11f-cfbf21554811) | ![產設系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/906a742d-ed37-488d-bf06-d8e0ce2d7020) | 

* Lane Detection System (Use ZED 2i Stereo Camera)


![類別_腳踏車_左](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/d792e0a2-0959-4fcd-b7b0-464404b84e1d)
