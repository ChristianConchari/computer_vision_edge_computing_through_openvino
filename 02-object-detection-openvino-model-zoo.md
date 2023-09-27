# Object Detection: OpenVINO Model Zoo
The Open Model Zoo for OpenVINO™ toolkit offers a diverse range of free, pre-trained deep learning models and demo applications, serving as complete templates for implementing deep learning in Python or C++. These resources can be found on the Open Model Zoo GitHub repository and are distributed under the Apache License Version 2.0.

## 1. Getting the OpenVINO Model Zoo
Through your terminal, navigate to the directory where you want to clone the OpenVINO Model Zoo repository and execute the following command:

```
git clone https://github.com/openvinotoolkit/open_model_zoo.git
```

Navigate to the directory where the repository was cloned. There you will find the following folders of interest:
- **demos**: Contains the demo applications that use the models from the Open Model Zoo.
- **models**: Contains the pre-trained models that can be used with the OpenVINO toolkit.

Inside the **models** folder, you will find the following folders:
- **intel**: Contains the pre-trained models from Intel.
- **public**: Contains the pre-trained models from the community.

## 2. Object detection with OpenVINO Model Zoo
In this section, we will use the OpenVINO Model Zoo to perform object detection on images and videos.

### 2.1 Downloading the pre-trained model
The OpenVINO Model Zoo contains a variety of pre-trained models that can be used for object detection. In this workshop, we will use the **person-vehicle-bike-detection-crossroad-1016** model, which is a pre-trained model that can detect people in images and videos. This model is located in the **intel** folder of the **models** folder.

To download the pre-trained model, first navigate to the **open_model_zoo\models\intel\person-vehicle-bike-detection-crossroad-1016** folder of the OpenVINO Model Zoo repository. Then, execute the following command:

```
omz_downloader --name person-vehicle-bike-detection-crossroad-1016
```

This command will download the model and its configuration files to the **open_model_zoo/models/intel/person-vehicle-bike-detection-crossroad-1016/intel/person-vehicle-bike-detection-crossroad-1016/** folder. Inside this folder, you will find the following files:
- **FP16**: Contains the model in the FP16 format.
- **FP16-INT8**: Contains the model in the FP16-INT8 format.
- **FP32**: Contains the model in the FP32 format.

The NCS2 device only supports the FP16 format, so we will use the model in the FP16 format. Inside the **FP16** folder, you will find the following files:

- **person-vehicle-bike-detection-crossroad-1016.bin**: Contains the weights of the model.  
- **person-vehicle-bike-detection-crossroad-1016.xml**: Contains the configuration of the model.

Copy both files to the **object_detection/resources/models** folder. 

Note that since the model was pre-trained by Intel, it is not necessary to perform additional conversion steps.

### 2.2 Running the object detection notebook
You can find the notebook for this section in [opevino_detection_model_zoo.ipynb](opevino_detection_model_zoo.ipynb). This notebook contains the code to perform object detection on images and using the pre-trained model that we downloaded in the previous section.

### 2.3 Running the object detection on videos script
You can find the script for this section in [video_object_detection.py](video_object_detection.py). This script contains the code to perform object detection on videos using the pre-trained model that we downloaded in the previous section.

To run the script, execute the following command in your terminal:

``` 
python video_object_detection.py -m -i resources/cars_1920x1080.mp4 -d MYRIAD
```

Try running the script with different videos and different devices. You can find some videos in the **resources** folder. And, get the available devices by running the following python command:

```python
from openvino.runtime import Core
ie = Core()
print(ie.available_devices)
```
-------
In this section, we learned how to use the OpenVINO Model Zoo to perform object detection on images and videos. In the next section, we will learn how to use the OpenVINO Model Optimizer to convert a custom model to the Intermediate Representation format.