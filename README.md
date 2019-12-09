# PlantSeedPrediction
Course Project for CS539[Machine Learning] in WPI

## Authors: 
Weinan Zhi, Yang Mo, Lei Ma, Zhiyi Huang, Yueqin Liang


## Project Description

## Dataset
### Plant Seedlings Dataset
The Original Dataset comes from [Plant Seedlings Dataset](https://arxiv.org/abs/1711.05458). In this project, [V1](https://vision.eng.au.dk/?download=/data/WeedData/Nonsegmented.zip) of the dataset is taken as input. The creater released a second version, [V2](https://vision.eng.au.dk/?download=/data/WeedData/NonsegmentedV2.zip), eliminating the problem that some of the images have more than one seeds. 
Here are some random samples of each spices:

![examples](examples.png)

## Preprocessing
### Data Preparation
Since the original dataset is not well normalized, Each image is cropped to 224 * 224 pixels resolution and RGB color theme.
For future classification task, three subsets are created as follow:

**trainingSet** 4750 RGB labeled images with 224\*224 resolution  

**sampleSet** 2371 RGB labeled images with 224\*224 resolution

**testSet** 794 RGB unlabeled images with 224\*224 resolution

After these process, here are several examples:
![regularized_images](preprocessed.png)

Since this project will performed on ResNet and DenseNet using Pytorch, the final outputs are transformed into tensor format by Pytorch. For the size purpose, the output is not uploaded, but the [data loader](https://github.com/WeinanZhi/-CS539-PlantSeedPrediction/blob/master/data_loader.ipynb) can do the job in no time and write the output to the current working directory.

The final output should consists of the following five files: 
![output_files](output.png)

**sample_X.pt** 2371 tensors corresponding to sampleSet 2371 images

**train_X.pt** 4750 tensors corresponding to trainingSet 4750 images

**test.pt** 794 tensors corresponding to testSet 794 images

**sample_Y.txt** 2371 labels corresponding to sample_X.pt 2371 tensors

**train_Y.txt** 4750 labels corresponding to train_X.pt 4750 tensors

### Data Segmentation
[Segmented Data](https://drive.google.com/drive/folders/19Px2relPjxfPZWV7UGHchqaqXX8RZBRc?usp=sharing)

## Transfer Learning of Image Classification

## DenseNet121 Model
The second model we used is DenseNet121 Model.
Compared with RESNET, densenet proposes a more radical dense connection mechanism. That is, all layers are connected to each other, especially, each layer will accept all the previous layers as its additional input.
![image](pics/des1.png)
The network structure of densenet is mainly composed of denseblock and transition. In denseblock, each layer has the same characteristic map size and can be connected in the channel dimension.
![image](pics/des2.png)



## Experiments

## Conclusion
We plot all the accuracy in one linechart as below, and get three conclusion.
1. Segmented data performed  better on ResNet18.
2. Segmented data  and original data performed  almost same  on Densenet121.
3. Densenet121 performed better than ResNet18 because of the complicated input structure.
![image](pics/linechart.png)

