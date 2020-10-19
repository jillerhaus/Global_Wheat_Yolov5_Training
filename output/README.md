# Global-Wheat-Detection: Yolov5 Training

This is the training part of my first solution to the [Global Wheat Detection](kaggle.com/c/global-wheat-detection) competition. This solution is based on YOLOv5, the solution consists of two parts: this training notebook and an [inference notebook](https://github.com/jillerhaus/Global_Wheat_Yolov5_Inference.git). This solution is very bare-bones, because while I was making it, YOLOv5 was banned from the competition, since it uses a GPL3 license. I brought this solution into a working state and then moved on to complete a compliant solution. Ultimately my solution was based on a PyTorch implementation of EfficienDet-D5. The [training](https://github.com/jillerhaus/Global_Wheat_EffDet_Training) and [inference](https://github.com/jillerhaus/Global_Wheat_EffDet_Inference) parts of this solution can both be found on my GitHub.



## Prerequisites

This project requires the Jupyter notebook containing the completed project, a pre-trained EfficientDet-D5 model used as a basis for training found in this [dataset](https://www.kaggle.com/mathurinache/efficientdet), as well as the [Global-Wheat-Detection dataset](https://www.kaggle.com/c/global-wheat-detection/data).

To run this project, you will need `Jupyter Notebooks` with a python 3 kernel to be installed on your machine. Instructions on how to install `Jupyter Notebooks` can be found on the [Jupyter website](https://jupyter.org/install).

The project itself is written in Python 3.7 and uses several different modules. To make it easier to use, a .yml file of the virtual anaconda environment I created for this solution will be included in this repository. Unfortunately some of the modules, such as NVIDIA Apex and the Pytorch implementation of EfficientDet itself need to be installed manually. Their repositories can be found in the attributions section of this readme. When using Windows, the pycocotools module will create issues. To remedy this, use `pip install pycocotools-windows`.

The file structure expected by the notebook is modeled after the Kaggle file structure, so that the notebook can be run on both Kaggle and Windows: The root directory should contain two directories, input and working. Place the extracted folder of both the datasets in input and the notebook in the working directories, respectively. This way the notebook will work without any changes to the code.

The notebook was used on Anaconda for Windows with both an NVIDIA 1050ti and a 2080ti. The settings used in the notebook are for the 2080ti and the `batch_size` attribute in the `TrainGlobalConfig` class needs to be adjusted for the amount of vram of the GPU used when training the model.



## Attributions

The network used the Pytorch implementation of EfficientDet by rwightman found [here](github.com/rwightman/efficientdet-pytorch@75c10c855a0bd617f9b6be0835761121e924b999). 

As a base to develop my code I used the [\[Training\] EfficientDet](https://www.kaggle.com/shonenkov/training-efficientdet) notebook by Alex Shonenkov. 

The pre-trained checkpoint the model is originally based on when training begins can be found [here](https://www.kaggle.com/mathurinache/efficientdet) and is the EfficientDet-D5 model in the dataset.

The cut and augmix data augmentation implementation is based on code by Kaggle User [nvnn](https://www.kaggle.com/nvnnghia)

To optimize the training process [NVIDIA Apex](https://github.com/NVIDIA/apex) was used.