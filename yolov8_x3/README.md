[YOLOv8](https://github.com/ultralytics/ultralytics) is a cutting-edge, state-of-the-art (SOTA) model that builds upon the success of previous YOLO versions and introduces new features and improvements to further boost performance and flexibility. YOLOv8 is designed to be fast, accurate, and easy to use, making it an excellent choice for a wide range of object detection and tracking, instance segmentation, image classification and pose estimation tasks.<br>

Horizon Algorithm Toolchain (also called OpenExplorer) is self-developed by Horizon Robotics to enable efficient and accurate model deployment onto the Horizon SoCs. It is released in the form of development package which can be obtained via [Horizon Algorithm Toolchain XJ3](https://developer.horizon.cc/forumDetail/136488103547258769) and [Horizon Algorithm Toolchain J5](https://developer.horizon.cc/forumDetail/118363912788935318).<br>

This project aims to deploy YOLOv8 models onto the Sunrise-3 SoCs of Horizon Robotics efficiently through Horizon Algorithm Toolchain. The deployment pipeline involves floating-point model training and exporting to ONNX format, model quantization and optimization, model compilation and model deployment (only model performance evaluation on board showed).<br>

## <div align="center">Quick Start</div>

<details open>
<summary>Install</summary>

#### YOLOv8
`yolov8_x3/ultralytics` folder contains the official YOLOv8 development tools along with the modified model structure that adapts to the Horizon platforms. For detailed model modification explanations, please see [Document]. Run the following commands to install:
```bash
cd yolov8_x3/ultralytics
pip install -r requirements.txt
python setup.py install
```

#### Horizon Algorithm Toolchain
Horizon Algorithm Toolchain provides Docker images to provide users with quick access to the tools. Simply run the `run_docker.sh` script:
```bash
sh run_docker.sh ./data/ gpu
```
This will specify the dataset path and run the docker in GPU mode (make sure that the GPU environment is properly set).

</details>

<details open>
<summary>Usage</summary>


#### Python

YOLOv8 may also be used directly in a Python environment, and accepts the same [arguments](https://docs.ultralytics.com/usage/cfg/) as in the CLI example above:

```python
from ultralytics import YOLO

# Load a model
model = YOLO("yolov8n.yaml")  # build a new model from scratch
model = YOLO("yolov8n.pt")  # load a pretrained model (recommended for training)

# Use the model
model.train(data="coco128.yaml", epochs=3)  # train the model
metrics = model.val()  # evaluate model performance on the validation set
results = model("https://ultralytics.com/images/bus.jpg")  # predict on an image
path = model.export(format="onnx")  # export the model to ONNX format
```

[Models](https://github.com/ultralytics/ultralytics/tree/main/ultralytics/cfg/models) download automatically from the latest Ultralytics [release](https://github.com/ultralytics/assets/releases). See YOLOv8 [Python Docs](https://docs.ultralytics.com/usage/python) for more examples.

</details>


