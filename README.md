# artificialYOLOtrainer

Clone the entire repository with the Darknet submodule by executing the following command:

``` 
git clone --recurse-submodules https://github.com/biparnakroy/artificialYOLOtrainer.git
```

If you already have the darknet built in your system then ommit ```--recurse-submodules```  and put your ```darknet```  directory inside the ```artificialYOLOtrainer``` directory

## Dependencies

### OS Enviornment

**artificalYOLOtrainer** has native support for *linux OS (ubuntu 20.04) with python 3.8.2* 

### Libraries

There are some library dependencies : opencv-python, numpy, math, argparse. 

You can install these libraries by executing the following command **(recomended)**

```
pip install -r requirements.txt
```
else you can also use:
```
pip install opencv-python
pip install numpy
pip install math
pip install argparse
```

## Building Darknet

If you already have darknet built in your system _(which is mostlikey the case because the main use of **artficialYOLOtrainer** to generate datasets using pretrained YOLO weights for further training of the model)_ then the following steps are not required.

**Note**: Make sure you have your ```darknet``` (prebuilt) directory inside the ```artificialYOLOtrainer``` directory.

However if dont't have darknet built in your system then ```cd in to the darknet directory``` and build darknet following [AlexyAB's guide](https://github.com/AlexeyAB/darknet/tree/3af6781de273fa01f4a535c8e40c5056e809e22f)

 Now we have to set up ```obj.names``` and ```obj.data``` files in ```data``` directory inside ```darknet```

 *obj.names:*
 The obj.names should contain the following:

 ```
 <class1>
 <class2>
  ....

 ```
 *obj.data:*
 The obj.data should cotain the following:
 ```
    classes= <number of classes>
    train  = data/train.txt
    valid = data/test.txt
    names = data/obj.names
    backup = ../new_weights
```
The ```train.txt``` and ```text.txt``` contains the the paths of images for training and test respectively.They will be configured when we are done generating the labels for our dataset and ready to retrain the model.

The ```backup= ../new_weights``` is basically to store the checkpoints of the weights generated on further traing. At this stage the new_weights directory should be empty. (even if you have darknet prebuilt then set the backup path to ../new_weights)




## Configuring pretrained weights

Put the pretrained yolo weights inside ```weights``` directory.

## Setting up the labels

Put the class labels (obj.names file used to train YOLO in Darknet) of your model in ```labels``` directory.

_In the labels directory there is already coco.names which contains the class labels of coco dataset_
