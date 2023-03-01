# DeepPose
DeepPose using MMPose
## Installation

Step 1: Download and install Miniconda (https://docs.conda.io/en/latest/miniconda.html) and Git (https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

Step 2: Create a conda environment and activate it.
```shell
conda create --name openmmlab python=3.8 -y
conda activate openmmlab
```

Step 3: Install PyTorch
```shell
conda install pytorch torchvision -c pytorch
```

Step 4: Install MMEngine and MMCV using MIM.
```shell
pip install -U openmim
mim install mmengine
mim install "mmcv>=2.0.0rc1"
```

Step 5: Install MMPose.
```shell
git clone https://github.com/open-mmlab/mmpose.git
cd mmpose
pip install -r requirements.txt
pip install -v -e .
# "-v" means verbose, or more output
# "-e" means installing a project in editable mode,
# thus any local modifications made to the code will take effect without reinstallation.
```

Step 6: Download config and checkpoint files.
```shell
mim download mmpose --config associative_embedding_hrnet_w32_coco_512x512  --dest .
```

Step 7: Install MMDetection.
```shell
cd..
git clone https://github.com/open-mmlab/mmdetection.git
cd mmdetection
pip install -v -e .
# "-v" means verbose, or more output
# "-e" means installing a project in editable mode,
# thus any local modifications made to the code will take effect without reinstallation.
```

Step 8: Download config and checkpoint files.
```shell
mim download mmdet --config yolov3_mobilenetv2_320_300e_coco --dest .
```

## Running the code

For webcam, running 
```shell
python demo/webcam_demo.py
```
Every time after restart the minicoda, run the following code will run the webcam_demo
```shell
conda activate openmmlab
cd mmpose
python demo/webcam_demo.py
```

## Coordinates of the key points

Adjustment was made to the file mmpose/mmpose/visulization/local_visualizer.py to generate a csv file including key points ID, name, time, X, Y, and confidence level.

## Errors might encountered:

1. Error appears saying "Building wheel for pycocotools (pyproject.toml) did not run successfully." and "ERROR: Could not build wheels for pycocotools, which is required to install pyproject.toml-based projects". 

The solution is download Microsoft Visual C++ 14.0 from https://visualstudio.microsoft.com/visual-cpp-build-tools/. After download the visual studio, install desktop development C++, and in the optional section on the right panel, select MSVCv143 - VS 2022 C++ x64/x86 build tools (Latest).

2. When running the demo, error appears saying "AssertionError: Torch not compiled with CUDA enabled".

Install CUDA from official website (https://developer.nvidia.com/cuda-downloads?target_os=Windows&target_arch=x86_64&target_version=11&target_type=exe_network), then tring to install pytorch again from official website (https://pytorch.org/get-started/locally/).

3. When running the demo, error appears saying "ImportError: cannot import name 'Config'"
Try intall MMDetection again by using
```shell
mim install "mmdet>=3.0.0rc0"
```
If this does not solve the issue, trying uninstall mmcv and mmcv-full first
```shell
mim uninstall mmcv
mim uninstall mmcv-full
```
Then reinstall the correct verison of mmcv from official website (https://mmcv.readthedocs.io/en/latest/get_started/installation.html).
