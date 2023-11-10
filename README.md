





# YOLACT-Building-AR
This study presents two major systems designed for automotive driver assistance. The first is a Forward Safety Warning System, which utilizes the [YOLACT](https://github.com/dbolya/yolact) real-time segmentation algorithm to identify the center point of objects ahead. It then calculates distances to these objects using 3D point cloud data from two [ZED 2i stereo cameras](https://www.stereolabs.com/zed-2i/) to provide warnings. The second system is an Augmented Reality Advertisement System for buildings. It employs the YOLACT segmentation algorithm to recognize buildings, estimates their approximate polygon sides and outer dimensions, and displays promotional videos for various campus departments using augmented reality techniques.

## YOLACT
[YOLACT](https://github.com/dbolya/yolact) is a real-time instance segmentation model that was proposed in 2019. It is a one-stage model, which means that it predicts the bounding boxes and masks of objects in a single pass. YOLACT achieves state-of-the-art results on the [COCO dataset](https://cocodataset.org/#home), while running at over 30 frames per second on a single GPU.

## Feature
* Introducing MobilenetV2 as the Backbone speeds up training and significantly reduces inference time.
* Utilizing two ZED 2i stereo cameras to achieve a wide-angle system and enable distance measurement.
* Detecting various departmental buildings within an effective distance through feature recognition,like the image below:

![建築物廣告系統介紹](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/f7158bb2-73d3-4bf1-96e9-7f45471cb996)


## Steps to run Code
### Create Virtual Environment
* Clone this repository and enter it:

        git clone https://github.com/KennyChen880127/YOLACT-Building-AR.git
* Goto cloned folder

        cd YOLACT-Building-AR
* Set up the environment using one of the following methods:
  - Using [Anaconda](https://www.anaconda.com/download)
    - Run: `conda env create -f environment.yml`
  - Manually with pip
    - Set up a Python3 environment (e.g., using virtenv).
    - Install [Pytorch](https://pytorch.org/get-started/previous-versions/) 1.0.1 (or higher) and TorchVision.
    - Install some other packages:

              # Cython needs to be installed before pycocotools
                pip install cython
                pip install opencv-python pillow pycocotools matplotlib 

### Predicting
This experiment introduced [MobilenetV2](https://arxiv.org/abs/1801.04381) as the backbone and has successfully trained on both COCO and architectural data.
* [MobilenetV2_COCO](https://drive.google.com/file/d/1twWZKKyLH_0DCBSD2aKgZJ3SDJqQPPUf/view?usp=sharing)
* [MobilenetV2_Building](https://drive.google.com/file/d/1Yk90LG1ul_WZBymxK1eKLcoHG-mqVXUl/view?usp=sharing)
* You can also use the models provided by YOLACT for prediction.
* Use the following command to predict:

        python predict.py --trained_model=weights/building_mobilenetv2_41_12000.pth --score_threshold=0.5 --top_k=1 --video_multiframe=4 --building_system=True --video=example_video/Electrical_Engineering.mp4 # "View the results in the example video."
        python predict.py --trained_model=weights/building_mobilenetv2_41_12000.pth --score_threshold=0.5 --top_k=1 --video_multiframe=4 --building_system=True --video='zed' # Using two ZED 2i stereo cameras as image input.
        python predict.py --trained_model=weights/building_mobilenetv2_41_12000.pth --score_threshold=0.5 --top_k=1 --video_multiframe=4 --building_system=True --video=0 # Display a webcam feed in real-time. If you have multiple webcams pass the index of the webcam you want instead of 0.
#### Notice
* When `--building_system=True`, the building recognition augmented reality system is activated.
* When `--building_system=False`, the road scene recognition (person, bicycle, car) is activated.
  - Forward Collision Warning can only be enabled when `--video='zed'`.
  - `--measure_distance=True` enables distance measurement.
  - `--FCW_system=True` enables Forward Collision Warning.
  - `--warning_distance=3.0` sets the safety distance, defaulting to 3.0 meters.
  
### Training
* To train, grab an imagenet-pretrained model and put it in `./weights`.
  - For MobileNetV2, download [mobilenet_v2-b0353104.pth](https://drive.google.com/file/d/1fgVOgqEm6PnaD_H51_INNQiLCsoN3Gh7/view?usp=sharing) from here.
* You can also use the pretrained weights provided by YOLACT.
* Use the following command to training with mobilenetv2:

          # Trains using the base config with a batch size of 32 (the default).
          python train.py --config=building_mobilenetv2_config --batch_size=32
  
### Results
* Building AR System

| Dept. of Electrical Engineering | Dept. of Mechanical Engineering | Dept. of Industrial Design | Dept. of Applied Foreign Languages | Dept. of Creative Design |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| ![電機系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/b0b34d5c-207e-4b43-8e81-2b9db21171b1) |![機械系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/89dd5aaa-7544-48ff-9ac6-3edd6ca4b4a2) | ![工設系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/5d4e1abb-a1f5-4d72-a39a-ddb4ae39ab69) | ![應外系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/9b7f23c0-062e-48b9-8fa3-22843b6d7fac) | ![產設系](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/28fd801c-e58a-4da7-a4ce-678ed58a3a09) | 

* Lane Detection System (Use ZED 2i Stereo Camera)

![類別_腳踏車_左](https://github.com/KennyChen880127/YOLACT-Building-AR/assets/99500847/1df63394-548c-4eff-a80b-02ad6977b988)

